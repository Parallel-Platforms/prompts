# Code Review Prompt

> Perform a thorough code review covering correctness,
> security, performance, and maintainability.

---

## Prompt

Review the following code changes. Provide feedback
organized by severity and category.

### Review Categories

Evaluate the code against these criteria:

#### 🔴 Critical (Must Fix)

- **Security vulnerabilities** — SQL injection, XSS, auth
  bypass, secrets exposure
- **Data loss risks** — Race conditions, missing
  transactions, unsafe deletes
- **Breaking changes** — API contracts, backward
  compatibility
- **Correctness bugs** — Logic errors that cause wrong
  behavior

#### 🟡 Important (Should Fix)

- **Error handling** — Missing try/catch, unhandled promise
  rejections, poor error messages
- **Performance issues** — N+1 queries, missing indexes,
  unnecessary re-renders, memory leaks
- **Test coverage** — Untested edge cases, missing
  integration tests
- **Type safety** — Any types, missing null checks, unsafe
  casts

#### 🔵 Suggestions (Consider)

- **Code clarity** — Confusing names, missing comments on
  complex logic
- **DRY violations** — Duplicated code that should be
  extracted
- **Consistency** — Deviations from project conventions
- **Simplification** — Overly complex solutions

#### ✅ Positive Feedback

- Well-structured code
- Good test coverage
- Clear naming and documentation
- Elegant solutions

### Review Format

Structure your review like this:

```markdown
## Summary

[One paragraph overall assessment]

## Critical Issues 🔴

### [Issue Title]

**File:** `path/to/file.ts` (lines X-Y) **Problem:**
[Description] **Fix:** [Suggested solution]

## Important Issues 🟡

[Same format]

## Suggestions 🔵

[Same format]

## What's Good ✅

[List positive aspects]

## Questions

[Any clarifying questions before approval]
```

### Checklist

Before approving, verify:

- [ ] No hardcoded secrets or credentials
- [ ] Error messages don't leak sensitive info
- [ ] User input is validated and sanitized
- [ ] Database queries are parameterized
- [ ] Async operations have proper error handling
- [ ] New dependencies are justified and audited
- [ ] Tests cover happy path and edge cases
- [ ] Documentation is updated if needed
- [ ] No console.log or debug code left in
- [ ] Feature flags are used for risky changes

### Context to Consider

- Is this a high-risk area (payments, auth, data deletion)?
- What's the blast radius if this code fails?
- Is this a hotfix (speed > perfection) or planned work?
- Who are the users affected by this code?
