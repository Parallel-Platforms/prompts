# Legacy Code Refactoring Prompt

> Safely refactor legacy code while preserving behavior and
> adding test coverage.

---

## Prompt

Help me refactor the legacy code I provide. Prioritize
safety and maintainability over speed.

### The Golden Rule

> **Make the change easy, then make the easy change.** —
> Kent Beck

### Refactoring Process

#### Phase 1: Understand

Before changing anything:

1. **Identify what the code does** — Not what it should do,
   what it actually does
2. **Find the inputs and outputs** — What goes in, what
   comes out
3. **Map the dependencies** — What does it call, what calls
   it
4. **Identify the risks** — What could break, who would
   notice

#### Phase 2: Characterize

Add tests that document current behavior:

```javascript
// Characterization test — documents existing behavior
describe('legacyFunction', () => {
  it('returns X when given Y (current behavior)', () => {
    // This test captures what the code DOES, not what it SHOULD do
    expect(legacyFunction(input)).toEqual(
      actualCurrentOutput
    );
  });
});
```

#### Phase 3: Refactor

Apply these techniques incrementally:

**Extract Method**

```javascript
// Before: Long method with multiple responsibilities
function processOrder(order) {
  // 50 lines of validation
  // 30 lines of calculation
  // 20 lines of formatting
}

// After: Extracted methods
function processOrder(order) {
  validateOrder(order);
  const total = calculateTotal(order);
  return formatOrderResponse(order, total);
}
```

**Introduce Parameter Object**

```javascript
// Before: Too many parameters
function createUser(
  name,
  email,
  age,
  role,
  department,
  startDate
) {}

// After: Parameter object
function createUser(userDetails) {}
```

**Replace Conditional with Polymorphism**

```javascript
// Before: Type checking
function getArea(shape) {
  if (shape.type === 'circle')
    return Math.PI * shape.radius ** 2;
  if (shape.type === 'rectangle')
    return shape.width * shape.height;
}

// After: Polymorphism
class Circle {
  getArea() {
    return Math.PI * this.radius ** 2;
  }
}
class Rectangle {
  getArea() {
    return this.width * this.height;
  }
}
```

**Replace Magic Numbers/Strings**

```javascript
// Before
if (user.role === 3) {
  /* admin logic */
}

// After
const ROLE_ADMIN = 3;
if (user.role === ROLE_ADMIN) {
  /* admin logic */
}
```

### Safety Checklist

Before each refactoring step:

- [ ] Tests pass
- [ ] Behavior is unchanged
- [ ] Change is small and reversible

After each step:

- [ ] Run tests
- [ ] Commit with clear message
- [ ] Verify in isolation

### Output Format

````markdown
## Refactoring Plan

### Current State Analysis

**Code Location:** `path/to/file.ts` **Lines:** X-Y
**Complexity:** [Low/Medium/High] **Test Coverage:**
[None/Partial/Good]

### Identified Issues

1. **[Issue]** — [Impact on maintainability]
2. **[Issue]** — [Impact]

### Proposed Changes

#### Step 1: Add Characterization Tests

[Tests to add before any changes]

#### Step 2: [First Refactoring]

**Technique:** [e.g., Extract Method] **Before:**

```javascript
// Current code
```
````

**After:**

```javascript
// Refactored code
```

**Risk:** [Low/Medium/High] **Verification:** [How to verify
behavior unchanged]

#### Step 3: [Next Refactoring]

[Continue pattern]

### Dependencies to Update

- [List any callers that need updates]

### Rollback Plan

[How to revert if issues found]

```

### When NOT to Refactor

- **No test coverage and can't add it** — Too risky
- **Don't understand the code** — Understand first
- **Deadline pressure** — Refactoring takes time
- **Code is being replaced soon** — Don't polish what you'll delete
- **Works fine, rarely changes** — "If it ain't broke..."
```
