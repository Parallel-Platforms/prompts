# Generate Inline Code Comments

Add clear, helpful inline comments to the provided code.

## Comment Guidelines

### When to Comment

**DO Comment:**
- **Complex Logic**: Explain non-obvious algorithms or business logic
- **Why, Not What**: Explain *why* the code does something, not *what* it does
- **Workarounds**: Explain hacks or workarounds and why they're necessary
- **Performance Optimizations**: Explain performance-critical sections
- **Non-Obvious Behavior**: Clarify unexpected or counterintuitive behavior
- **External Dependencies**: Explain assumptions about external systems
- **Edge Cases**: Document special case handling
- **TODOs**: Mark incomplete or temporary code

**DON'T Comment:**
- **Obvious Code**: Don't explain what clear, self-documenting code already shows
- **Redundant Comments**: Don't repeat what the code clearly states
- **Obsolete Comments**: Remove or update outdated comments
- **Commented-Out Code**: Remove old code instead of commenting it out

### Comment Style

#### Function/Method Comments
```javascript
/**
 * Calculates the total price including tax and discounts.
 * 
 * @param {number} basePrice - The base price before tax and discounts
 * @param {number} taxRate - Tax rate as a decimal (e.g., 0.08 for 8%)
 * @param {number} discountPercent - Discount percentage (0-100)
 * @returns {number} The final price after tax and discounts
 * @throws {Error} If basePrice is negative or taxRate is invalid
 * 
 * @example
 * calculateTotal(100, 0.08, 10) // Returns 97.20
 */
```

#### Inline Comments
```javascript
// Use binary search for O(log n) performance on sorted array
const index = binarySearch(sortedArray, target);

// HACK: API sometimes returns null instead of empty array
// Remove this workaround after backend fix (Issue #123)
const items = response.data || [];

// Edge case: Handle timezone offset for date comparison
const normalizedDate = new Date(date.getTime() + date.getTimezoneOffset() * 60000);
```

#### Block Comments
```javascript
/*
 * Authentication Flow:
 * 1. User submits credentials
 * 2. Validate against database
 * 3. Generate JWT token with 1-hour expiration
 * 4. Store refresh token in secure cookie
 * 5. Return access token to client
 */
```

#### TODO Comments
```javascript
// TODO: Add retry logic for failed network requests
// TODO(username): Optimize this query - currently O(n²)
// FIXME: This breaks on Safari < 14 - need polyfill
// HACK: Temporary workaround until API v2 is released
```

### Language-Specific Formats

**JavaScript/TypeScript**: JSDoc, inline `//`, block `/* */`

**Python**: Docstrings `"""`, inline `#`

**Java**: JavaDoc `/** */`, inline `//`

**Swift**: Documentation `///`, inline `//`

**Kotlin**: KDoc `/** */`, inline `//`

**C#**: XML Documentation `///`, inline `//`

## Best Practices
- Write comments as complete sentences
- Keep comments up-to-date with code changes
- Use proper grammar and spelling
- Be concise but clear
- Use examples for complex concepts
- Link to external documentation when relevant
- Use consistent comment style throughout the codebase

## Special Cases

### Regular Expressions
```javascript
// Match email format: username@domain.extension
// Supports: a-z, 0-9, dots, hyphens in username
const emailRegex = /^[a-z0-9.-]+@[a-z0-9.-]+\.[a-z]{2,}$/i;
```

### Magic Numbers
```javascript
// Maximum retry attempts before giving up
const MAX_RETRIES = 3;

// API timeout in milliseconds (30 seconds)
const TIMEOUT_MS = 30000;
```

### Complex Conditions
```javascript
// Only show notification if:
// - User is active (not in do-not-disturb mode)
// - Notification is high priority OR user enabled all notifications
// - User hasn't exceeded daily notification limit
if (user.isActive && 
    (notification.isHighPriority || user.allowAllNotifications) && 
    user.notificationCount < DAILY_LIMIT) {
  showNotification(notification);
}
```

Please add comments that:
1. Improve code understanding
2. Explain the "why" behind decisions
3. Are concise and clear
4. Follow the project's commenting conventions
5. Add value without being redundant
