# PR Description Generator Prompt

> Generate clear, comprehensive pull request descriptions
> from code changes.

---

## Prompt

Analyze my code changes and generate a pull request
description.

### Analyze the Changes

Look at the diff and identify:

1. **What changed** — Files modified, added, deleted
2. **Why it changed** — The purpose/motivation
3. **How it works** — Key implementation details
4. **What to test** — How reviewers can verify it works

### Generate PR Description

Use this format:

```markdown
## Summary

[2-3 sentences explaining what this PR does and why]

## Changes

- [Bullet point for each logical change]
- [Group related file changes together]
- [Focus on WHAT, not HOW]

## Type of Change

- [ ] 🐛 Bug fix (non-breaking change that fixes an issue)
- [ ] ✨ New feature (non-breaking change that adds
      functionality)
- [ ] 💥 Breaking change (fix or feature that breaks
      existing functionality)
- [ ] 📝 Documentation update
- [ ] 🔧 Refactor (no functional changes)
- [ ] 🧪 Test update

## How to Test

1. [Step-by-step instructions]
2. [Include test data if needed]
3. [Expected results]

## Screenshots

[If UI changes, describe what screenshots should show]

## Checklist

- [ ] My code follows the project's style guidelines
- [ ] I have performed a self-review
- [ ] I have added tests that prove my fix/feature works
- [ ] New and existing tests pass locally
- [ ] I have updated documentation as needed

## Related Issues

Closes #[issue number]

## Notes for Reviewers

[Any context that would help reviewers, areas of concern, or
questions]
```

### Adapt Based on Change Type

**For bug fixes, include:**

- Root cause analysis
- How to reproduce the bug
- How the fix addresses it

**For new features, include:**

- User story or requirement reference
- Design decisions made
- Future considerations

**For refactors, include:**

- Motivation for the refactor
- Before/after comparison if helpful
- Proof that behavior is unchanged

**For breaking changes, include:**

- Migration guide
- Affected consumers
- Rollback plan

### Keep It Scannable

- Use bullet points over paragraphs
- Bold key terms
- Keep summary under 3 sentences
- Link to docs/tickets rather than duplicating info
