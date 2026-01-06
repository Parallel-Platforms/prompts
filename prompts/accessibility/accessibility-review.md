# Accessibility Review

Review the code for accessibility compliance and provide recommendations.

## WCAG 2.1 Compliance

### Level A (Minimum)
- **Keyboard Access**: All functionality available via keyboard
- **Text Alternatives**: Alt text for images, labels for inputs
- **Audio/Video**: Captions and transcripts provided
- **Color**: Information not conveyed by color alone
- **Contrast**: Minimum contrast ratios met

### Level AA (Recommended)
- **Enhanced Contrast**: 4.5:1 for normal text, 3:1 for large text
- **Resize Text**: Text can be resized up to 200% without loss of functionality
- **Multiple Ways**: Multiple ways to find pages (navigation, search, sitemap)
- **Headings and Labels**: Descriptive headings and labels
- **Focus Visible**: Keyboard focus indicator is visible

### Level AAA (Enhanced)
- **High Contrast**: 7:1 for normal text, 4.5:1 for large text
- **Sign Language**: Sign language interpretation for videos
- **Extended Audio Description**: Extended audio descriptions for videos

## Semantic HTML

### Structure
- **Landmarks**: Use semantic landmarks (`<header>`, `<nav>`, `<main>`, `<footer>`)
- **Headings**: Proper heading hierarchy (h1 → h2 → h3, no skipping)
- **Lists**: Use `<ul>`, `<ol>`, `<dl>` for lists
- **Tables**: Use `<table>` with proper headers for tabular data
- **Buttons vs Links**: Use `<button>` for actions, `<a>` for navigation

### Forms
```html
<!-- Good: Accessible form -->
<label for="email">Email Address</label>
<input 
  type="email" 
  id="email" 
  name="email"
  aria-describedby="email-help"
  required
>
<span id="email-help">We'll never share your email</span>
```

- **Labels**: All inputs have associated labels
- **Required Fields**: Clearly marked and programmatically indicated
- **Error Messages**: Associated with inputs via `aria-describedby`
- **Fieldsets**: Group related inputs with `<fieldset>` and `<legend>`

## ARIA (Accessible Rich Internet Applications)

### When to Use ARIA
- **Enhance Native HTML**: Only when native HTML is insufficient
- **Custom Widgets**: For complex interactive components
- **Live Regions**: For dynamic content updates
- **State Management**: Indicate component states

### ARIA Best Practices
```html
<!-- Custom button -->
<div role="button" tabindex="0" aria-pressed="false">
  Toggle
</div>

<!-- Alert -->
<div role="alert" aria-live="assertive">
  Your session will expire in 5 minutes
</div>

<!-- Modal dialog -->
<div role="dialog" aria-labelledby="dialog-title" aria-modal="true">
  <h2 id="dialog-title">Confirm Action</h2>
  <!-- dialog content -->
</div>
```

### Common ARIA Attributes
- **aria-label**: Accessible name for elements
- **aria-labelledby**: Reference to label element
- **aria-describedby**: Additional description
- **aria-hidden**: Hide decorative elements from screen readers
- **aria-live**: Announce dynamic content changes
- **aria-expanded**: Indicate expandable/collapsible state
- **aria-current**: Indicate current item in navigation
- **aria-disabled**: Indicate disabled state

## Keyboard Navigation

### Focus Management
- **Tab Order**: Logical tab order following visual flow
- **Focus Indicators**: Visible focus indicators for all interactive elements
- **Skip Links**: Skip to main content link
- **Focus Trapping**: Modal dialogs trap focus appropriately
- **Auto-focus**: Appropriate use of autofocus

### Keyboard Patterns
- **Enter/Space**: Activate buttons and links
- **Arrow Keys**: Navigate menus, tabs, radio groups
- **Escape**: Close modals, dropdowns, tooltips
- **Home/End**: Navigate to start/end of lists
- **Tab/Shift+Tab**: Navigate between focusable elements

```javascript
// Example: Accessible keyboard handler
element.addEventListener('keydown', (e) => {
  switch(e.key) {
    case 'Enter':
    case ' ': // Space
      e.preventDefault();
      activate();
      break;
    case 'Escape':
      close();
      break;
    case 'ArrowDown':
      e.preventDefault();
      focusNext();
      break;
    case 'ArrowUp':
      e.preventDefault();
      focusPrevious();
      break;
  }
});
```

## Screen Reader Support

### Text Content
- **Alt Text**: Descriptive alt text for images
- **Empty Alt**: Empty alt (`alt=""`) for decorative images
- **Icon Labels**: Text labels or aria-label for icon-only buttons
- **Abbreviations**: Expand abbreviations with `<abbr title="">`

### Announcements
- **Live Regions**: Use `aria-live` for dynamic updates
- **Status Messages**: Use `role="status"` for non-critical updates
- **Alerts**: Use `role="alert"` for important messages
- **Loading States**: Announce loading and completion

### Hidden Content
```html
<!-- Visually hidden but available to screen readers -->
<span class="sr-only">Search</span>

<!-- Hidden from screen readers -->
<span aria-hidden="true">🔍</span>

CSS:
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border-width: 0;
}
```

## Color & Contrast

### Contrast Ratios
- **Normal Text**: Minimum 4.5:1 (AA), 7:1 (AAA)
- **Large Text**: Minimum 3:1 (AA), 4.5:1 (AAA)
- **UI Components**: Minimum 3:1 for boundaries
- **Graphics**: Minimum 3:1 for essential graphics

### Color Usage
- **Not Color Alone**: Don't rely on color only to convey information
- **Error States**: Use icons/text in addition to red color
- **Links**: Underline links or provide other visual distinction
- **Charts**: Use patterns in addition to colors

## Mobile Accessibility

### Touch Targets
- **Minimum Size**: 44x44 CSS pixels (48x48 recommended)
- **Spacing**: Adequate spacing between touch targets
- **Feedback**: Visual/haptic feedback on touch

### Gestures
- **Alternative Methods**: Provide alternatives to complex gestures
- **Swipe Actions**: Make swipe actions discoverable
- **Pinch/Zoom**: Support pinch-to-zoom unless justified

### Orientation
- **Support Both**: Support portrait and landscape orientations
- **No Lock**: Don't lock orientation unless essential
- **Responsive**: Content adapts to orientation changes

## Multimedia

### Images
- **Alt Text**: Descriptive alternative text
- **Complex Images**: Long descriptions for complex images
- **Decorative Images**: Empty alt for decorative images
- **SVG**: Use `<title>` and `<desc>` for accessible SVGs

### Video/Audio
- **Captions**: Closed captions for all videos
- **Transcripts**: Text transcripts for audio content
- **Audio Description**: Describe visual-only content
- **Controls**: Accessible media player controls

## Forms & Validation

### Error Handling
- **Clear Messages**: Clear, specific error messages
- **Error Location**: Indicate which field has an error
- **Error Association**: Associate errors with fields
- **Success Messages**: Confirm successful submissions

### Input Assistance
- **Instructions**: Clear instructions before inputs
- **Help Text**: Additional help text where needed
- **Format Examples**: Show expected input format
- **Autocomplete**: Use autocomplete attributes appropriately

## Testing Checklist

### Automated Testing
- [ ] Run axe DevTools or similar accessibility scanner
- [ ] Check HTML validation
- [ ] Verify ARIA usage
- [ ] Test color contrast ratios

### Manual Testing
- [ ] Navigate entire site using only keyboard
- [ ] Test with screen reader (NVDA, JAWS, VoiceOver)
- [ ] Test at 200% zoom level
- [ ] Test with different color modes (dark mode, high contrast)
- [ ] Disable CSS and verify content is still logical
- [ ] Test with images disabled
- [ ] Verify form error handling

### Assistive Technology
- [ ] Screen readers: NVDA (Windows), JAWS (Windows), VoiceOver (Mac/iOS)
- [ ] Voice control: Dragon NaturallySpeaking, Voice Control (iOS)
- [ ] Screen magnification: ZoomText, built-in OS magnifiers
- [ ] Keyboard-only navigation

## Common Issues to Check

### Critical Issues
- Missing alt text on images
- Form inputs without labels
- Low color contrast
- Keyboard traps
- Missing skip links
- Auto-playing media without controls

### Important Issues
- Improper heading hierarchy
- Non-descriptive link text ("click here")
- Missing focus indicators
- Unclear error messages
- Missing ARIA labels on custom components
- Inaccessible modals/dialogs

## Recommendations Format

For each issue found:
1. **Issue**: Description of the accessibility problem
2. **WCAG Criterion**: Which WCAG criterion is violated (e.g., 1.1.1, 2.4.6)
3. **Level**: A, AA, or AAA
4. **Impact**: Who is affected and how
5. **Location**: Where in the code the issue occurs
6. **Fix**: Specific code changes needed
7. **Example**: Code example of the fix

Please provide a comprehensive accessibility review with actionable recommendations.
