# Generate Integration Tests

Generate integration tests for the provided code that verify component interactions and system behavior.

## Test Scope

### Component Integration
- **API Integration**: Test interactions with backend APIs
- **Database Integration**: Test data persistence and retrieval
- **Service Integration**: Test communication between services
- **Third-Party Integration**: Test external service integrations

### End-to-End Flows
- **User Workflows**: Test complete user journeys
- **Data Flow**: Test data flow through the system
- **State Management**: Test state changes across components
- **Error Propagation**: Test how errors are handled across boundaries

## Test Requirements

### Realistic Scenarios
- Use realistic test data
- Simulate actual user interactions
- Test concurrent operations where applicable
- Test timeout and retry scenarios

### Environment Setup
- **Test Database**: Use a test database or in-memory database
- **Mock External Services**: Mock third-party APIs appropriately
- **Test Configuration**: Use appropriate test environment configuration
- **Cleanup**: Ensure proper cleanup after tests

### Assertions
- Verify expected outcomes
- Check side effects
- Validate state changes
- Confirm data persistence

## Best Practices
- **Isolation**: Each test should be independent
- **Idempotent**: Tests should be repeatable
- **Clear Failure Messages**: Provide descriptive failure messages
- **Performance**: Consider test execution time
- **Maintainability**: Keep tests maintainable as code evolves

## Testing Considerations
- Test both success and failure paths
- Include timeout handling
- Test transaction boundaries
- Verify rollback behavior on errors
- Check for resource leaks

Please generate integration tests that:
1. Cover critical integration points
2. Are reliable and deterministic
3. Provide clear feedback on failures
4. Follow the project's testing patterns
