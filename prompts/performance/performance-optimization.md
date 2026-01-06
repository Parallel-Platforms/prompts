# Performance Optimization Review

Analyze the code for performance issues and provide optimization recommendations.

## Performance Metrics

### Key Metrics to Consider
- **Time to First Byte (TTFB)**: Server response time
- **First Contentful Paint (FCP)**: When first content appears
- **Largest Contentful Paint (LCP)**: When main content is visible
- **Time to Interactive (TTI)**: When page becomes fully interactive
- **Cumulative Layout Shift (CLS)**: Visual stability
- **First Input Delay (FID)**: Responsiveness to user input

### Performance Budgets
- **JavaScript Bundle**: < 200KB gzipped
- **CSS**: < 50KB gzipped
- **Images**: Optimized and appropriately sized
- **Fonts**: < 100KB total
- **LCP**: < 2.5s
- **FID**: < 100ms
- **CLS**: < 0.1

## Frontend Performance

### JavaScript Optimization

#### Bundle Size
- **Code Splitting**: Split code into smaller chunks
- **Tree Shaking**: Remove unused code
- **Lazy Loading**: Load components on demand
- **Dynamic Imports**: Use `import()` for code splitting
- **Remove Unused Dependencies**: Audit and remove unnecessary packages

```javascript
// Code splitting example
const HeavyComponent = lazy(() => import('./HeavyComponent'));

// Dynamic import
button.addEventListener('click', async () => {
  const module = await import('./feature.js');
  module.initialize();
});
```

#### Execution Performance
- **Avoid Long Tasks**: Break up long-running operations
- **Debounce/Throttle**: Limit expensive event handlers
- **Web Workers**: Move heavy computation off main thread
- **Virtual Scrolling**: For long lists
- **Memoization**: Cache expensive calculations

```javascript
// Debounce example
const debouncedSearch = debounce((query) => {
  performSearch(query);
}, 300);

// Memoization example
const memoizedExpensiveFunction = useMemo(() => {
  return expensiveCalculation(data);
}, [data]);
```

### Rendering Performance

#### React/Vue/Angular Specific
- **Avoid Unnecessary Re-renders**: Use React.memo, useMemo, useCallback
- **Key Props**: Use stable keys for lists
- **Component Splitting**: Break large components into smaller ones
- **Virtualization**: Use react-window or similar for long lists
- **Lazy Loading**: Lazy load components not immediately needed

```javascript
// React optimization
const MemoizedComponent = memo(({ data }) => {
  const expensiveValue = useMemo(() => {
    return processData(data);
  }, [data]);
  
  return <div>{expensiveValue}</div>;
});
```

#### DOM Manipulation
- **Batch DOM Updates**: Minimize reflows and repaints
- **DocumentFragment**: Use for multiple insertions
- **CSS Classes**: Change classes instead of individual styles
- **Avoid Layout Thrashing**: Batch reads and writes

```javascript
// Good: Batch DOM updates
const fragment = document.createDocumentFragment();
items.forEach(item => {
  const el = createItemElement(item);
  fragment.appendChild(el);
});
container.appendChild(fragment);
```

### CSS Performance

#### Rendering Optimization
- **Avoid Expensive Properties**: Be careful with box-shadow, filter, opacity
- **Use Transform/Opacity**: For animations (GPU-accelerated)
- **Contain**: Use CSS containment for independent subtrees
- **Will-Change**: Hint browser about upcoming changes
- **Reduce Selector Complexity**: Avoid deep nesting

```css
/* Good: GPU-accelerated animation */
.element {
  transform: translateX(100px);
  transition: transform 0.3s;
}

/* Use containment */
.card {
  contain: layout style paint;
}
```

#### Load Performance
- **Critical CSS**: Inline critical CSS
- **Remove Unused CSS**: Use PurgeCSS or similar tools
- **Minification**: Minify and compress CSS
- **CSS Modules**: Scope styles to components

### Image Optimization

#### Format & Compression
- **Modern Formats**: Use WebP, AVIF with fallbacks
- **Appropriate Size**: Serve images at display size
- **Compression**: Optimize JPEG/PNG compression
- **SVG**: Use SVG for icons and simple graphics
- **Lazy Loading**: Use `loading="lazy"` attribute

```html
<!-- Responsive images -->
<picture>
  <source srcset="image.avif" type="image/avif">
  <source srcset="image.webp" type="image/webp">
  <img src="image.jpg" alt="Description" loading="lazy">
</picture>

<!-- Responsive with srcset -->
<img 
  srcset="small.jpg 400w, medium.jpg 800w, large.jpg 1200w"
  sizes="(max-width: 400px) 100vw, (max-width: 800px) 50vw, 33vw"
  src="medium.jpg"
  alt="Description"
>
```

### Network Optimization

#### Resource Loading
- **HTTP/2**: Use HTTP/2 for multiplexing
- **CDN**: Serve static assets from CDN
- **Compression**: Enable gzip/brotli compression
- **Caching**: Set appropriate cache headers
- **Preload**: Preload critical resources
- **Prefetch**: Prefetch likely next resources
- **DNS Prefetch**: Resolve DNS early for external domains

```html
<!-- Preload critical resources -->
<link rel="preload" href="critical.css" as="style">
<link rel="preload" href="critical.js" as="script">

<!-- Prefetch next page -->
<link rel="prefetch" href="/next-page.html">

<!-- DNS prefetch -->
<link rel="dns-prefetch" href="https://api.example.com">
```

#### API Optimization
- **Minimize Requests**: Combine related API calls
- **Pagination**: Implement pagination for large datasets
- **GraphQL**: Use GraphQL to fetch only needed data
- **Caching**: Cache API responses appropriately
- **Compression**: Compress API responses
- **Partial Updates**: Send only changed data

```javascript
// Request batching
const batchedFetch = async (ids) => {
  const response = await fetch('/api/items', {
    method: 'POST',
    body: JSON.stringify({ ids }),
  });
  return response.json();
};
```

### Font Optimization

#### Loading Strategy
- **font-display**: Use `font-display: swap` or `optional`
- **Subset Fonts**: Include only needed characters/weights
- **Preload Fonts**: Preload critical fonts
- **System Fonts**: Consider system font stack
- **Variable Fonts**: Use variable fonts to reduce requests

```css
@font-face {
  font-family: 'CustomFont';
  src: url('font.woff2') format('woff2');
  font-display: swap;
  unicode-range: U+0000-00FF; /* Subset */
}
```

## Backend Performance

### Database Optimization

#### Query Optimization
- **Indexes**: Add indexes for frequently queried fields
- **N+1 Queries**: Use eager loading to avoid N+1 problems
- **Query Complexity**: Simplify complex queries
- **Projection**: Select only needed fields
- **Connection Pooling**: Use database connection pooling

```javascript
// Bad: N+1 query problem
const users = await User.findAll();
for (const user of users) {
  user.posts = await Post.findAll({ where: { userId: user.id } });
}

// Good: Eager loading
const users = await User.findAll({
  include: [Post]
});
```

#### Caching
- **Query Caching**: Cache expensive query results
- **Redis/Memcached**: Use in-memory caching
- **Cache Invalidation**: Implement proper cache invalidation
- **TTL**: Set appropriate time-to-live values

### API Performance

#### Response Optimization
- **Compression**: Enable gzip/brotli compression
- **Pagination**: Implement cursor-based pagination
- **Field Selection**: Allow clients to select fields
- **Rate Limiting**: Protect against abuse
- **Response Caching**: Cache responses with ETags

```javascript
// Pagination example
app.get('/api/items', async (req, res) => {
  const { cursor, limit = 20 } = req.query;
  const items = await getItems({ cursor, limit });
  res.json({
    data: items,
    nextCursor: items.length === limit ? items[items.length - 1].id : null
  });
});
```

#### Background Processing
- **Async Operations**: Move slow operations to background jobs
- **Queue System**: Use message queues (RabbitMQ, Redis Queue)
- **Webhooks**: Use webhooks instead of polling
- **Batch Processing**: Process items in batches

## Mobile-Specific Performance

### App Performance
- **Startup Time**: Minimize app launch time
- **Memory Usage**: Monitor and optimize memory usage
- **Battery Usage**: Minimize battery drain
- **Network Usage**: Optimize data transfer
- **Image Loading**: Use progressive loading for images

### Native Features
- **List Virtualization**: Use FlatList (React Native) or RecyclerView (Android)
- **Image Caching**: Implement image caching
- **Bundle Size**: Optimize bundle size and use code splitting
- **Native Modules**: Use native modules for performance-critical code
- **Animations**: Use native driver for animations

```javascript
// React Native: Native driver animation
Animated.timing(fadeAnim, {
  toValue: 1,
  duration: 300,
  useNativeDriver: true, // Enable native driver
}).start();
```

## Performance Monitoring

### Tools & Metrics
- **Lighthouse**: Automated audits
- **Chrome DevTools**: Performance profiling
- **WebPageTest**: Real-world performance testing
- **Real User Monitoring (RUM)**: Track real user metrics
- **Synthetic Monitoring**: Automated performance checks

### Profiling
- **CPU Profiling**: Identify expensive operations
- **Memory Profiling**: Find memory leaks
- **Network Analysis**: Optimize network requests
- **Bundle Analysis**: Analyze bundle composition

```javascript
// Performance marks
performance.mark('operation-start');
// ... expensive operation ...
performance.mark('operation-end');
performance.measure('operation', 'operation-start', 'operation-end');
```

## Common Performance Issues

### JavaScript
- Large bundle sizes
- Unnecessary re-renders
- Memory leaks
- Synchronous operations blocking UI
- Inefficient event handlers
- Large dependency trees

### CSS
- Unused CSS
- Complex selectors
- Layout thrashing
- Non-GPU accelerated animations
- Large stylesheets

### Images
- Unoptimized images
- Wrong format
- No lazy loading
- No responsive images
- Missing compression

### Network
- Too many requests
- No caching
- Large payloads
- Render-blocking resources
- No compression

## Optimization Checklist

- [ ] Minimize and bundle JavaScript
- [ ] Implement code splitting and lazy loading
- [ ] Optimize images (format, size, lazy loading)
- [ ] Enable compression (gzip/brotli)
- [ ] Implement caching strategy
- [ ] Use CDN for static assets
- [ ] Optimize CSS (remove unused, minimize)
- [ ] Reduce third-party script impact
- [ ] Optimize web fonts
- [ ] Minimize main thread work
- [ ] Implement virtual scrolling for long lists
- [ ] Database query optimization
- [ ] API response optimization
- [ ] Implement performance monitoring

Please provide:
1. Identified performance bottlenecks
2. Specific optimization recommendations
3. Expected performance improvements
4. Implementation priorities
5. Measurement strategy to verify improvements
