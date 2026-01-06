# Contributing

Thanks for contributing to the prompts repository!

## Adding a New Prompt

### File Naming

Use the format: `[action]-[subject].prompt.md`

Examples:

- `setup-agents-md.prompt.md`
- `generate-tests.prompt.md`
- `review-api-design.prompt.md`

### Prompt Structure

Every prompt should follow this structure:

```markdown
# [Title]

> [One-line description of what this prompt does]

---

## Prompt

[The actual prompt content, written in second person]

### [Section 1]

[Details...]

### [Section 2]

[Details...]
```

### Guidelines

1. **Be specific** — Vague prompts get vague results
2. **Be framework-agnostic** — Unless the prompt is
   specifically for a framework
3. **Include examples** — Show what good output looks like
4. **Use markdown formatting** — Headers, lists, code
   blocks, tables
5. **Test your prompt** — Try it with at least two different
   AI assistants

### What Makes a Good Prompt

- Solves a common, recurring problem
- Works across different AI assistants
- Produces consistent, high-quality output
- Includes clear success criteria
- Can be used without modification (or with minimal
  customization)

### What to Avoid

- Prompts that require proprietary context
- Prompts specific to one codebase
- Prompts that produce inconsistent results
- Overly long prompts (>500 lines)

## Submitting

1. Fork this repository
2. Add your prompt file
3. Update the README.md table
4. Submit a pull request with a description of the prompt's
   purpose
