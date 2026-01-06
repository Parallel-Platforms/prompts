# Mobile-Specific Code Review

Review this mobile application code with focus on mobile-specific concerns:

## Platform Compatibility
- **Cross-Platform**: If using React Native, Flutter, or similar, does the code work on both iOS and Android?
- **Platform-Specific Code**: Are platform-specific implementations properly isolated and documented?
- **API Level Compatibility**: Does the code handle different API levels/OS versions appropriately?

## Performance
- **Battery Life**: Does the code minimize battery drain (e.g., efficient location tracking, background tasks)?
- **Network Usage**: Is network usage optimized (e.g., batching requests, caching, compression)?
- **Memory Management**: Are there potential memory leaks? Is memory usage optimized for mobile constraints?
- **App Size**: Does the code contribute unnecessarily to app bundle size?

## User Experience
- **Offline Support**: Does the app handle offline scenarios gracefully?
- **Loading States**: Are loading states and progress indicators implemented?
- **Responsive Design**: Does the UI work across different screen sizes and orientations?
- **Touch Interactions**: Are touch targets appropriately sized? Are gestures intuitive?

## Mobile Best Practices
- **Permissions**: Are runtime permissions requested appropriately and handled correctly?
- **Background Processing**: Are background tasks implemented efficiently?
- **Push Notifications**: If applicable, are notifications implemented properly?
- **Deep Linking**: If applicable, are deep links handled correctly?

## Security
- **Data Storage**: Is sensitive data stored securely (keychain/keystore)?
- **API Keys**: Are API keys and secrets properly secured?
- **SSL Pinning**: Is certificate pinning implemented where necessary?
- **Input Validation**: Is user input properly validated and sanitized?

Please provide specific mobile development recommendations and best practices.
