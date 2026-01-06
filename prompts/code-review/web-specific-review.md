# Web-Specific Code Review

Review this web application code with focus on web-specific concerns:

## Browser Compatibility
- **Cross-Browser Support**: Does the code work across major browsers (Chrome, Firefox, Safari, Edge)?
- **Polyfills**: Are necessary polyfills included for older browsers?
- **Progressive Enhancement**: Does the app work with JavaScript disabled (where appropriate)?
- **Feature Detection**: Are modern features properly feature-detected rather than browser-detected?

## Performance
- **Bundle Size**: Is the JavaScript bundle optimized and code-split appropriately?
- **Lazy Loading**: Are routes and components lazy-loaded where beneficial?
- **Caching**: Are appropriate caching strategies implemented?
- **Image Optimization**: Are images properly optimized and responsive?
- **Critical Rendering Path**: Is the critical rendering path optimized?

## Accessibility (a11y)
- **Semantic HTML**: Is semantic HTML used appropriately?
- **ARIA Attributes**: Are ARIA attributes used correctly and only when necessary?
- **Keyboard Navigation**: Can all interactive elements be accessed via keyboard?
- **Screen Reader Support**: Will screen readers properly announce content?
- **Color Contrast**: Does the UI meet WCAG color contrast requirements?

## SEO
- **Meta Tags**: Are appropriate meta tags present (title, description, Open Graph)?
- **Structured Data**: Is structured data (JSON-LD) implemented where beneficial?
- **Semantic Markup**: Is content marked up semantically for search engines?
- **Server-Side Rendering**: If using SSR/SSG, is it implemented correctly?

## Security
- **XSS Prevention**: Is user input properly sanitized to prevent XSS attacks?
- **CSRF Protection**: Are CSRF tokens implemented for state-changing operations?
- **Content Security Policy**: Is CSP configured appropriately?
- **HTTPS**: Are all resources loaded over HTTPS?
- **Third-Party Scripts**: Are third-party scripts loaded securely?

## Responsive Design
- **Mobile-First**: Is the design mobile-first?
- **Viewport**: Is the viewport meta tag properly configured?
- **Responsive Images**: Are images responsive with appropriate srcset/sizes?
- **Touch-Friendly**: Are interactive elements touch-friendly on mobile?

## Best Practices
- **State Management**: Is state managed efficiently and predictably?
- **API Integration**: Are API calls properly handled with loading/error states?
- **Forms**: Are forms accessible, validated, and user-friendly?
- **Error Boundaries**: Are error boundaries implemented to catch React errors?

Please provide specific web development recommendations and best practices.
