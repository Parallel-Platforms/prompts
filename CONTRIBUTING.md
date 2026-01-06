# Contributing to Prompts Library

Thank you for your interest in contributing to the Prompts Library! This document provides guidelines for adding new prompts or improving existing ones.

## How to Contribute

### 1. Finding Something to Work On

- **New Prompts**: Check if there are any prompt categories or use cases not currently covered
- **Improvements**: Review existing prompts and suggest enhancements
- **Bug Fixes**: Fix typos, formatting issues, or incorrect information
- **Documentation**: Improve README or add examples

### 2. Submitting Changes

1. **Fork the Repository**
   ```bash
   # Fork via GitHub UI, then clone your fork
   git clone https://github.com/YOUR-USERNAME/prompts.git
   cd prompts
   ```

2. **Create a Branch**
   ```bash
   git checkout -b add-new-prompt-name
   # or
   git checkout -b improve-existing-prompt
   ```

3. **Make Your Changes**
   - Add or edit prompt files
   - Follow the guidelines below
   - Test your prompts with AI assistants

4. **Commit Your Changes**
   ```bash
   git add .
   git commit -m "Add [prompt name] for [use case]"
   # or
   git commit -m "Improve [prompt name]: [brief description]"
   ```

5. **Push to Your Fork**
   ```bash
   git push origin add-new-prompt-name
   ```

6. **Create a Pull Request**
   - Go to the original repository on GitHub
   - Click "New Pull Request"
   - Select your branch
   - Fill in the PR template with details about your changes

## Prompt Guidelines

### File Structure

Each prompt should be a markdown file in the appropriate category directory:

```
prompts/
├── code-review/
├── testing/
├── documentation/
├── security/
├── accessibility/
├── performance/
└── [new-category]/
```

### Prompt Format

A good prompt should include:

1. **Clear Title** - Descriptive h1 heading
2. **Purpose Statement** - Brief description of what the prompt does
3. **Structured Sections** - Organized with h2/h3 headings
4. **Specific Criteria** - Detailed checklist of what to look for
5. **Examples** - Code examples where helpful
6. **Output Format** - How the AI should structure its response

### Example Prompt Structure

```markdown
# [Prompt Title]

[Brief description of what this prompt does and when to use it]

## [Main Category 1]

### [Subcategory]
- **Item 1**: Description and what to check
- **Item 2**: Description and what to check
- **Item 3**: Description and what to check

### Code Examples (if applicable)
\`\`\`javascript
// Good example
const goodCode = "demonstrates best practice";

// Bad example
const badCode = "demonstrates anti-pattern";
\`\`\`

## [Main Category 2]

### [Subcategory]
- Checklist item
- Another checklist item

## Output Requirements

Please provide:
1. Specific finding or recommendation
2. Code location (if applicable)
3. Suggested fix with example
4. Priority level (if applicable)
```

### Writing Best Practices

#### DO:
- ✅ Write clear, concise instructions
- ✅ Use bullet points for easy scanning
- ✅ Include specific examples
- ✅ Cover both common and edge cases
- ✅ Use consistent formatting
- ✅ Focus on actionable items
- ✅ Make prompts technology-agnostic when possible
- ✅ Test prompts with real code before submitting

#### DON'T:
- ❌ Use vague or ambiguous language
- ❌ Include overly complex jargon without explanation
- ❌ Create prompts that are too narrow/specific
- ❌ Duplicate existing prompts
- ❌ Include outdated best practices
- ❌ Make assumptions about tech stack (unless category-specific)

### Naming Conventions

**Files**: Use lowercase with hyphens
- ✅ `generate-unit-tests.md`
- ✅ `security-review.md`
- ❌ `GenerateUnitTests.md`
- ❌ `security_review.md`

**Directories**: Use lowercase with hyphens
- ✅ `code-review/`
- ✅ `accessibility/`
- ❌ `codeReview/`
- ❌ `Accessibility/`

## Categories

### Existing Categories

- **code-review**: Code quality, best practices, style
- **testing**: Unit, integration, E2E test generation
- **documentation**: README, API docs, comments
- **security**: Security audits, vulnerability detection
- **accessibility**: WCAG compliance, inclusive design
- **performance**: Optimization, profiling, monitoring

### Adding New Categories

If your prompt doesn't fit existing categories:

1. Create a new directory under `prompts/`
2. Add your prompt file(s) to the new directory
3. Update the README.md to include the new category
4. In your PR, explain why the new category is needed

## Quality Checklist

Before submitting, ensure your prompt:

- [ ] Has a clear, descriptive title
- [ ] Includes a purpose statement
- [ ] Uses consistent markdown formatting
- [ ] Contains specific, actionable criteria
- [ ] Includes examples where helpful
- [ ] Follows the naming conventions
- [ ] Has been tested with an AI assistant
- [ ] Doesn't duplicate existing prompts
- [ ] Is placed in the appropriate category
- [ ] Updates the README if adding new category

## Testing Your Prompt

Before submitting:

1. **Test with AI Assistant**: Try your prompt with ChatGPT, GitHub Copilot, or another AI assistant
2. **Use Real Code**: Test on actual code samples, not just hypotheticals
3. **Check Output Quality**: Ensure the AI provides useful, actionable feedback
4. **Iterate**: Refine the prompt based on the quality of responses
5. **Get Feedback**: Ask colleagues to review your prompt

## Examples of Good Contributions

### New Prompt Example
```
Add GraphQL schema validation prompt

This PR adds a new prompt for reviewing GraphQL schemas, focusing on:
- Type definitions and relationships
- Query performance considerations
- Security best practices (depth limiting, cost analysis)
- Documentation completeness

Tested with ChatGPT on several production GraphQL schemas.
```

### Improvement Example
```
Improve mobile-specific review prompt

Updates:
- Added iOS 17 and Android 14 specific considerations
- Included SwiftUI and Jetpack Compose best practices
- Enhanced battery optimization section
- Added examples for common issues

Tested with real mobile apps.
```

## Code of Conduct

- Be respectful and constructive
- Welcome newcomers and help them get started
- Focus on the content, not the contributor
- Assume good intentions
- Keep discussions on-topic

## Questions?

If you have questions about contributing:

1. Check existing issues and PRs
2. Review the README and existing prompts
3. Open an issue with your question
4. Tag it with `question` label

## Recognition

All contributors will be recognized in the project. Thank you for helping make this resource better for the developer community!

---

**Remember**: Quality over quantity. One well-crafted, tested prompt is more valuable than several untested ones.
