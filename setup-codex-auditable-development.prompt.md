# Codex Auditable Development (CAD) Setup Prompt

> Use this prompt to set up Codex Auditable Development in
> any project. Copy this entire file and paste it to an AI
> assistant.

---

## Prompt

I want to implement **Codex Auditable Development (CAD)** in
this project. Codices are plain-language documents that
describe how the code currently works — its logic, behavior,
and business rules. They help product teams understand the
actual system behavior (good, bad, and ugly) without reading
code.

### Core Principles

1. **Code is the source of truth** — Codices document what
   the code actually does, not what we wish it did
2. **If code and codex disagree, update the codex** — The
   codex must reflect current system behavior
3. **Engineering owns codices; product consumes them** —
   Engineers maintain accuracy, product gains visibility
4. **Written for product people** — Use plain business
   language that PMs, designers, and stakeholders can read
   without technical context
5. **No technical content** — No code, no implementation
   details, no technical jargon
6. **Gherkin scenarios validate behavior** — Formal
   Given/When/Then syntax for testable rules

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

   ````markdown
   # [Topic] Rules

   > [One-line description of what this codex covers.]

   ## Rules

   1. **Rule name** — Description of the rule
   2. **Rule name** — Description of the rule

   ## [Optional: Domain-Specific Sections]

   (Tables, workflows, field requirements as needed)

   ## Scenarios

   ```gherkin
   Scenario: [Descriptive name]
     Given [precondition]
     When [action]
     Then [expected outcome]
   ```
   ````

   ```

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
- **Scenarios:** Gherkin syntax in fenced code blocks
- **Plain business language only:** No code, no technical
  jargon, no implementation details
- **Audience is product people:** Write so PMs, designers,
  and stakeholders understand without engineering context
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
- Technical specifications or architecture decisions
- Code patterns or engineering standards
- API contracts or data schemas

### Codex Maintenance Rules

Add these to AGENTS.md to keep codices in sync with code:

```markdown
### ⛔ Codex Maintenance Rules

**Codices must accurately reflect the code.** Keep them in
sync with actual system behavior.

1. **When code changes, update the codex** — After modifying
   behavior, update the relevant codex to match
2. **If code contradicts a codex**, update the CODEX to
   reflect what the code actually does — then flag the
   discrepancy to product
3. **Before changing behavior**, check if a codex documents
   it and notify the user:
   > "This change affects behavior documented in
   > `[codex-file]`. I'll update the codex to reflect the
   > new behavior."
4. **Codices are documentation, not policy** — They describe
   reality, not aspirations
```

### Example Codex

````markdown
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

```gherkin
Scenario: Password too short
  Given a user enters a password shorter than 8 characters
  When the form is submitted
  Then the system shows "Password must be at least 8 characters"

Scenario: Account lockout after failed attempts
  Given a user has failed login 4 times
  When the user fails login a 5th time
  Then the account is locked for 30 minutes
  And an email notification is sent to the user
```
````

```

---

## Start Here

Please analyze my codebase and:

1. List the major domains that need codices
2. Propose a folder structure
3. Ask me which domains to prioritize
4. Create the codices one domain at a time

Let's begin!
```
