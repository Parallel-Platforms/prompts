# Test Generation Prompt

> Generate comprehensive unit and integration tests for
> existing code.

---

## Prompt

Generate tests for the code I provide. Create thorough test
coverage following best practices.

### Analyze the Code First

Before writing tests, identify:

1. **Public API** — Functions, methods, and classes to test
2. **Input variations** — Valid inputs, edge cases, invalid
   inputs
3. **Dependencies** — What needs to be mocked
4. **Side effects** — External calls, state changes, events
5. **Error paths** — How the code can fail

### Test Structure

Organize tests using this pattern:

```
describe('[Unit Under Test]', () => {
  describe('[Method/Function]', () => {
    describe('when [scenario]', () => {
      it('should [expected behavior]', () => {
        // Arrange
        // Act
        // Assert
      });
    });
  });
});
```

### What to Test

#### ✅ Always Test

- **Happy path** — Normal, expected usage
- **Edge cases** — Empty arrays, zero values, max values,
  boundaries
- **Error handling** — Invalid input, missing data, network
  failures
- **Null/undefined** — Nullable parameters and return values
- **Type coercion** — String "0" vs number 0 if relevant

#### ⚠️ Test When Applicable

- **Async behavior** — Promises, timeouts, race conditions
- **State changes** — Before/after mutations
- **Event emissions** — Callbacks, event handlers
- **Integration points** — API calls, database queries (with
  mocks)

#### ❌ Don't Test

- Private implementation details
- Third-party library internals
- Getters/setters with no logic
- Framework boilerplate

### Naming Convention

Use descriptive test names that read like specifications:

```javascript
// ✅ Good
it('should return empty array when input is empty');
it(
  'should throw ValidationError when email format is invalid'
);
it('should retry 3 times before failing');

// ❌ Bad
it('works');
it('test email');
it('handles error');
```

### Mocking Guidelines

```javascript
// Mock external dependencies, not the unit under test
// Use dependency injection when possible
// Verify mock interactions when side effects matter

// Example structure:
const mockDependency = {
  method: vi.fn().mockResolvedValue(expectedResult),
};

const result = await unitUnderTest(mockDependency);

expect(mockDependency.method).toHaveBeenCalledWith(
  expectedArgs
);
expect(result).toEqual(expectedResult);
```

### Test Categories to Generate

1. **Unit tests** — Isolated function/method tests
2. **Integration tests** — Multiple units working together
3. **Error tests** — Verify error handling and messages
4. **Boundary tests** — Min/max values, empty inputs

### Output Format

```javascript
import {
  describe,
  it,
  expect,
  vi,
  beforeEach,
} from 'vitest';
import { functionUnderTest } from './module';

describe('functionUnderTest', () => {
  // Setup
  beforeEach(() => {
    vi.clearAllMocks();
  });

  // Happy path
  describe('when given valid input', () => {
    it('should return expected result', () => {
      const result = functionUnderTest(validInput);
      expect(result).toEqual(expectedOutput);
    });
  });

  // Edge cases
  describe('edge cases', () => {
    it('should handle empty input', () => {
      const result = functionUnderTest([]);
      expect(result).toEqual([]);
    });
  });

  // Error cases
  describe('error handling', () => {
    it('should throw when input is null', () => {
      expect(() => functionUnderTest(null)).toThrow(
        'Input is required'
      );
    });
  });
});
```

### Adapt to Project

- Match the existing test framework (Jest, Vitest, Mocha,
  pytest, etc.)
- Follow project naming conventions
- Use project's assertion style
- Match project's mocking patterns
