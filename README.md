# Prompts Library

A curated collection of AI prompts designed to streamline mobile and web development workflows. These prompts are optimized for use with GitHub Copilot, ChatGPT, and other AI coding assistants.

## 📚 Available Prompts

### Code Review
Comprehensive code review prompts to ensure code quality and best practices.

- **[General Code Review](prompts/code-review/general-code-review.md)** - Overall code quality, maintainability, and best practices
- **[Mobile-Specific Review](prompts/code-review/mobile-specific-review.md)** - Mobile app development concerns (iOS, Android, React Native, Flutter)
- **[Web-Specific Review](prompts/code-review/web-specific-review.md)** - Web development concerns (browser compatibility, SEO, responsive design)

### Testing
Prompts for generating comprehensive test suites.

- **[Generate Unit Tests](prompts/testing/generate-unit-tests.md)** - Create thorough unit tests with edge cases and mocks
- **[Generate Integration Tests](prompts/testing/generate-integration-tests.md)** - Create integration tests for component interactions
- **[Generate E2E Tests](prompts/testing/generate-e2e-tests.md)** - Create end-to-end tests simulating user workflows

### Documentation
Prompts for creating clear, comprehensive documentation.

- **[Generate README](prompts/documentation/generate-readme.md)** - Create professional README documentation
- **[Generate API Docs](prompts/documentation/generate-api-docs.md)** - Create comprehensive API documentation
- **[Generate Inline Comments](prompts/documentation/generate-inline-comments.md)** - Add helpful code comments and documentation

### Security
Security-focused prompts to identify and fix vulnerabilities.

- **[Security Review](prompts/security/security-review.md)** - Comprehensive security audit for common vulnerabilities
- **[Dependency Security Audit](prompts/security/dependency-security-audit.md)** - Audit dependencies for known vulnerabilities

### Accessibility
Prompts to ensure applications are accessible to all users.

- **[Accessibility Review](prompts/accessibility/accessibility-review.md)** - WCAG compliance and accessibility best practices

### Performance
Prompts to optimize application performance.

- **[Performance Optimization](prompts/performance/performance-optimization.md)** - Analyze and optimize frontend and backend performance

## 🚀 How to Use

### With GitHub Copilot

1. Open a file you want to review or improve
2. Add a comment with the prompt content from any of the markdown files
3. Let Copilot generate suggestions based on the prompt

Example:
```javascript
// Review this code for security issues:
// [Paste security review prompt here]

function processUserInput(input) {
  // Your code here
}
```

### With ChatGPT or Other AI Assistants

1. Copy the prompt from the desired markdown file
2. Paste it into your AI assistant chat
3. Follow up with your code or specific questions

Example:
```
[Paste the prompt]

Here's my code:
[Your code]
```

### Direct Integration

Many prompts can be referenced directly by URL in AI coding tools:

```
https://raw.githubusercontent.com/Parallel-Platforms/prompts/main/prompts/code-review/general-code-review.md
```

## 💡 Best Practices

- **Be Specific**: When using prompts, provide specific code or context
- **Iterate**: Use multiple prompts in sequence for comprehensive analysis
- **Combine Prompts**: Mix and match prompts for thorough reviews
- **Customize**: Adapt prompts to your project's specific needs
- **Review Output**: Always review AI-generated suggestions critically

## 🤝 Contributing

We welcome contributions! To add new prompts or improve existing ones:

1. Fork the repository
2. Create a new branch for your changes
3. Add or update prompts following the existing format
4. Ensure prompts are clear, comprehensive, and well-structured
5. Submit a pull request with a description of your changes

### Prompt Guidelines

When creating prompts:
- Use clear, descriptive headers and sections
- Include specific examples where helpful
- Cover both common and edge cases
- Follow markdown best practices
- Make prompts technology-agnostic when possible
- Include context about when to use the prompt

## 📖 Prompt Categories

- **Code Review**: Quality, style, and best practice reviews
- **Testing**: Test generation for various testing levels
- **Documentation**: Generate user and developer documentation
- **Security**: Security audits and vulnerability detection
- **Accessibility**: WCAG compliance and inclusive design
- **Performance**: Optimization recommendations for speed and efficiency

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🌟 Why Use These Prompts?

- **Consistency**: Ensure consistent code reviews across your team
- **Comprehensive**: Cover all aspects of development (security, performance, accessibility)
- **Time-Saving**: Automated reviews catch issues early
- **Educational**: Learn best practices through AI feedback
- **Quality**: Improve code quality and maintainability
- **Mobile & Web Focused**: Tailored for mobile and web development challenges

## 🔗 Related Resources

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [WCAG Guidelines](https://www.w3.org/WAI/WCAG21/quickref/)
- [Web.dev Performance](https://web.dev/performance/)
- [React Native Best Practices](https://reactnative.dev/docs/performance)
- [MDN Web Docs](https://developer.mozilla.org/)

---

**Note**: These prompts are designed to assist developers, not replace human judgment. Always review and validate AI-generated suggestions before applying them to production code.
