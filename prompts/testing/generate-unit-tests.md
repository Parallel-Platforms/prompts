# Generate Unit Tests

Generate comprehensive unit tests for the provided code.

## Test Requirements

### Coverage
- **Happy Path**: Test all expected use cases with valid inputs
- **Edge Cases**: Test boundary conditions and edge cases
- **Error Cases**: Test error handling and invalid inputs
- **Null/Undefined**: Test behavior with null, undefined, and empty values

### Test Structure
- **Arrange-Act-Assert**: Structure tests using the AAA pattern
- **Descriptive Names**: Use clear, descriptive test names that explain what is being tested
- **Single Responsibility**: Each test should verify one specific behavior
- **Independent Tests**: Tests should not depend on each other or execution order

### Best Practices
- **Mock External Dependencies**: Mock API calls, database operations, and external services
- **Deterministic**: Tests should produce consistent results regardless of when they run
- **Fast**: Tests should execute quickly
- **Maintainable**: Tests should be easy to understand and update

## Testing Framework Considerations
- Use the project's existing testing framework (Jest, Vitest, JUnit, XCTest, etc.)
- Follow the project's testing conventions and patterns
- Include necessary setup and teardown
- Use appropriate assertions and matchers

## What to Include
- Setup/teardown if needed
- Mock configurations
- Test data and fixtures
- Clear test descriptions
- Comments for complex test scenarios

Please generate unit tests that are:
1. Comprehensive and thorough
2. Easy to read and maintain
3. Following testing best practices
4. Consistent with the project's existing test style
