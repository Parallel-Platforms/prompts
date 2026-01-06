# Generate E2E Tests

Generate end-to-end tests that validate the application from a user's perspective.

## Test Framework
Use the project's E2E testing framework (Cypress, Playwright, Detox, Appium, Selenium, etc.)

## Test Coverage

### User Journeys
- **Critical Paths**: Test the most important user workflows
- **Authentication**: Login, logout, registration, password recovery
- **Core Features**: Test primary application features
- **Form Submissions**: Test data entry and validation
- **Navigation**: Test navigation between screens/pages

### User Interactions
- **Click/Tap**: Button clicks, link clicks, touch interactions
- **Input**: Text input, form filling, file uploads
- **Gestures**: Swipe, pinch, zoom (for mobile)
- **Keyboard**: Keyboard navigation and shortcuts
- **Drag and Drop**: If applicable

### Validation
- **Visual Feedback**: Verify UI updates and loading states
- **Error Messages**: Verify error message display
- **Success Messages**: Verify confirmation messages
- **Data Persistence**: Verify data is saved correctly
- **State Consistency**: Verify application state remains consistent

## Best Practices

### Selectors
- Use data-testid attributes for reliable selectors
- Avoid brittle selectors (CSS classes, positions)
- Use accessible selectors where possible
- Document custom selector strategies

### Wait Strategies
- Wait for elements to be visible/clickable
- Wait for network requests to complete
- Use explicit waits over implicit waits
- Handle dynamic content appropriately

### Test Data
- Use fixtures for consistent test data
- Clean up test data after tests
- Handle data dependencies
- Use unique identifiers to avoid conflicts

### Error Handling
- Take screenshots on failure
- Record videos for debugging
- Log detailed error information
- Retry flaky operations appropriately

## Test Structure
- **Given**: Setup initial state and preconditions
- **When**: Execute user actions
- **Then**: Verify expected outcomes

## Mobile-Specific (if applicable)
- Test on multiple device sizes
- Test different orientations
- Test platform-specific behaviors
- Test offline scenarios
- Test deep links

## Web-Specific (if applicable)
- Test on multiple browsers
- Test responsive layouts
- Test PWA features
- Test accessibility features

Please generate E2E tests that:
1. Simulate realistic user interactions
2. Are reliable and not flaky
3. Provide meaningful failure information
4. Cover critical user workflows
5. Are maintainable and well-documented
