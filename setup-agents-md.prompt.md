# AGENTS.md Setup Prompt

> Create an AGENTS.md file to guide AI coding assistants
> working in your repository.

---

## Prompt

I want you to create an **AGENTS.md** file for this project.
AGENTS.md is a standard file that AI coding assistants read
to understand project conventions, constraints, and context.

### Analyze My Codebase

First, analyze the repository to understand:

1. **Tech stack** — Languages, frameworks, libraries
2. **Project structure** — Key directories and their
   purposes
3. **Coding conventions** — Naming, formatting, patterns in
   use
4. **Testing approach** — Test framework, coverage
   expectations
5. **Build/deploy process** — How the project is built and
   deployed

### Create AGENTS.md

Create an `AGENTS.md` file in the repository root with these
sections:

```markdown
# AGENTS.md

> Instructions for AI coding assistants working in this
> repository.

## Project Overview

[One paragraph describing what this project does]

## Tech Stack

- **Language:** [e.g., TypeScript 5.x]
- **Framework:** [e.g., React 18, Next.js 14]
- **Testing:** [e.g., Vitest, React Testing Library]
- **Package Manager:** [e.g., pnpm]

## Project Structure
```

/src /components — React components /hooks — Custom React
hooks /lib — Utility functions /types — TypeScript types
/tests — Test files

```

## Coding Conventions

### Naming

- Components: PascalCase (`UserProfile.tsx`)
- Hooks: camelCase with `use` prefix (`useAuth.ts`)
- Utils: camelCase (`formatDate.ts`)
- Types: PascalCase with no prefix (`User`, not `IUser`)

### File Organization

[Describe how files should be organized]

### Patterns to Follow

[List patterns used in this codebase]

### Anti-Patterns to Avoid

[List things NOT to do]

## Testing Requirements

- All new features must have tests
- Minimum coverage: [X]%
- Use [testing pattern] for [type of test]

## Before Submitting Code

1. Run `[lint command]`
2. Run `[test command]`
3. Run `[build command]`

## Key Files

| File | Purpose |
|------|---------|
| `[file]` | [description] |

## Domain Knowledge

[Any business logic or domain concepts the AI should understand]

## Common Tasks

### Adding a new component

[Step-by-step instructions]

### Adding a new API endpoint

[Step-by-step instructions]
```

### Customization

After generating the initial AGENTS.md, ask me if I want to:

1. Add protected files/directories (files the AI should
   never modify)
2. Add workflow-specific instructions
3. Include links to codex files (if using CAD)
4. Add team-specific conventions

### Keep It Maintainable

- Keep AGENTS.md under 300 lines
- Focus on what's different or non-obvious about this
  project
- Don't duplicate info that's in package.json or
  tsconfig.json
- Update it when major conventions change
