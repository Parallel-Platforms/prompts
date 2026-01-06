# Codex Auditable Development (CAD) Setup Prompt

> Use this prompt to set up Codex Auditable Development in
> any project. Copy this entire file and paste it to an AI
> assistant.

---

## Prompt

I want to implement **Codex Auditable Development (CAD)** in
this project. Codices are plain-language policy documents
that define system rules. They serve as the canonical source
of truth for how the application behaves.

### Core Principles

1. **Codices are the source of truth** — If code and codex
   disagree, the codex is correct
2. **Product owns codices; engineering enforces them**
3. **Codices define rules, not implementations**
4. **Written for humans** — Product managers, designers, and
   engineers can all read them
5. **BDD scenarios validate behavior** — Given/When/Then
   format for testable rules

### What I Need You To Do

1. **Analyze my codebase** to identify major domains that
   need policy documentation (e.g., authentication,
   authorization, validation, workflows)

2. **Create a `/codices` folder structure** organized by
   domain:

   ```
   /codices
     README.md
     /authentication
       login.codex.md
     /authorization
       roles.codex.md
     /[domain]
       [topic].codex.md
   ```

3. **Write codices** using this standard format:

   ```markdown
   # [Topic] Rules

   > [One-line description of what this codex covers.]

   ## Rules

   1. **Rule name** — Description of the rule
   2. **Rule name** — Description of the rule

   ## [Optional: Domain-Specific Sections]

   (Tables, workflows, field requirements as needed)

   ## Scenarios

   ### Scenario: [Descriptive name]

   - **Given** [precondition]
   - **When** [action]
   - **Then** [expected outcome]
   ```

4. **Update AGENTS.md** (or create one) with:

   - Codex file index table
   - Key rules quick reference
   - Policy protection rules (prevent accidental edits)

5. **Create a validation prompt** at
   `.github/validate-against-codex.prompt.md`

### Codex Format Guidelines

- **Title:** Always ends with "Rules" (e.g., "Login Rules")
- **Intro:** One-line blockquote starting with "Defines..."
- **Rules section:** Numbered list — the core policies
- **Scenarios:** BDD-style Given/When/Then at the end
- **No code blocks:** Use plain language
- **Tables:** Use for permissions, statuses, field
  requirements
- **Cardinal rules:** Use `> ⚠️` callout for critical
  policies

### What Makes a Good Codex

Create a codex when:

- The rule applies across multiple screens or features
- The rule affects visibility, permissions, or lifecycle
- The rule introduces invariants ("this must always be
  true")
- The rule would be costly or dangerous to misinterpret
- AI agents need to understand it without guessing

Do NOT create codices for:

- Styling or visual polish
- One-off experiments
- Internal refactors
- Implementation details (those go in docs/)

### Policy Protection Rules

Add these to AGENTS.md to prevent accidental codex edits:

```markdown
### ⛔ Policy Protection Rules

**Codices are protected documents.** Do NOT modify them
during normal feature work or bug fixes.

1. **Never edit codex files** unless the user explicitly
   requests a "policy change" or "update the codex"
2. **If code contradicts a codex**, fix the CODE not the
   codex - then flag the discrepancy to the user
3. **If a feature requires a policy change**, STOP and ask:
   > "This would require changing the policy in
   > `[codex-file]`. Do you want to update the policy?"
4. **Wait for explicit confirmation** before modifying any
   `.codex.md` file
```

### Example Codex

```markdown
# Password Rules

> Defines password requirements and reset policies.

## Rules

1. **Minimum length is 8 characters**
2. **Must contain at least one number**
3. **Must contain at least one special character**
4. **Passwords expire after 90 days** for admin accounts
5. **Failed attempts lock account** after 5 tries

## Reset Flow

| Step | Action                     | Timeout |
| ---- | -------------------------- | ------- |
| 1    | User requests reset        | —       |
| 2    | Email sent with magic link | 15 min  |
| 3    | User sets new password     | —       |
| 4    | All sessions invalidated   | —       |

## Scenarios

### Scenario: Password too short

- **Given** user enters "Pass1!"
- **When** form is validated
- **Then** error: "Password must be at least 8 characters"

### Scenario: Account lockout

- **Given** user has failed login 4 times
- **When** user fails login a 5th time
- **Then** account is locked for 30 minutes
- **And** email notification sent to user
```

---

## Start Here

Please analyze my codebase and:

1. List the major domains that need codices
2. Propose a folder structure
3. Ask me which domains to prioritize
4. Create the codices one domain at a time

Let's begin!
