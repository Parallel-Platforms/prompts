Codex Enhancement Prompt

I need you to comprehensively expand codex documentation
files for the Puff Club platform. These codices are
plain-language business rule documents written for
non-technical product owners, PMs, and stakeholders to
understand ground-truth code behavior.

Your Task: Review and dramatically expand codex files to be
complete, authoritative references for all business logic,
user flows, validation rules, and edge cases.

Required Structure for Each Codex:

Rules Section (40-55+ rules organized into 6-8 categories)

Group related rules under clear category headers Use
numbered lists for easy reference Write in plain language
avoiding technical jargon Cover: core behavior, validation,
permissions, state management, error handling, edge cases
Multiple Mermaid Diagrams (3-5 diagrams minimum)

Main user flow (flowchart showing complete journey) State
transitions (if applicable) Error handling flow (decision
tree) Integration flows (data flow between components) Use
clear labels, decision points, and outcomes Detailed Tables
(5-10+ tables)

Field specifications with validation rules State matrices
showing all possible states and transitions Error messages
with conditions Permission matrices (who can do what) API
parameters and responses Sort/filter options Comprehensive
Gherkin Scenarios (25-35+ scenarios)

Cover happy path (5-8 scenarios) Cover validation failures
(5-8 scenarios) Cover edge cases (5-8 scenarios) Cover
permissions/access control (3-5 scenarios) Cover integration
points (3-5 scenarios) Use Given-When-Then format with
detailed tables Research Process:

Read the original codex file Use semantic_search to find
implementation files Use grep_search to find specific
patterns Use read_file to study detailed implementation
Identify ALL gaps between current codex and actual code
behavior Writing Guidelines:

**Non-technical language:** Translate ALL technical terms to
business language

- "MongoDB ObjectId" → "system-generated unique ID" or
  "24-character identifier"
- "bcrypt hash" → "encrypted password" or "password
  encryption"
- "async/await" → "background process" or "waiting for
  result"
- "JWT token" → "authentication token" or "login credential"
- "API endpoint" → "system service" or just describe what it
  does
- "Promise" → "waiting for result"
- "Database collection" → "dedicated storage area" or just
  "database"
- In diagrams: use "System checks...", "User submits...",
  not "API validates...", "Controller processes..."

**Product owner perspective:** Write for decision-makers who
need to:

- Understand what users can and cannot do
- Explain constraints to customers
- Make product decisions about features
- Communicate timelines and tradeoffs
- Focus on BEHAVIOR and OUTCOMES, not implementation details

**Explain the "why" behind design decisions:**

- Why does token expire in 10 minutes? (Security vs user
  convenience tradeoff)
- Why identical responses? (Prevent attackers from
  discovering valid emails)
- Why no automatic logout? (User convenience, password reset
  might be from different device)
- Connect technical decisions to business value

**Complete coverage:** Don't leave gaps - document every
validation, every error state, every edge case

- What happens at exactly the boundary? (10 minutes vs
  10:01)
- What happens if user does action twice?
- What happens during concurrent operations?
- What happens if external service fails?

**Examples everywhere:** Use concrete examples in rules,
tables, and scenarios

- Use realistic email addresses: "user@example.com", not
  "email"
- Use real-looking tokens: "507f1f77bcf86cd799439011", not
  "{token}"
- Use actual error messages: "Password must be at least 8
  characters"
- Show what user sees, not what code returns

**Visual aids:** Prefer mermaid diagrams over text
descriptions of flows

- Label diagram nodes with user actions and outcomes: "User
  clicks reset link", "Show password form"
- Avoid technical labels: not "POST /auth/reset", instead
  "Submit password reset request"

**Comprehensive Gherkin Scenarios (25-35+ scenarios)**

Scenario categories to cover:

- Happy path (5-8 scenarios) - successful user journeys from
  start to finish
- Validation failures (5-8 scenarios) - what gets rejected
  and why, with exact error messages
- Edge cases (5-8 scenarios) - boundary conditions, timing
  issues, concurrent operations
- Security scenarios (3-5 scenarios) - attack prevention,
  enumeration, token theft attempts
- Integration points (3-5 scenarios) - interactions with
  external services, mobile app, email
- Error recovery (2-4 scenarios) - what happens when things
  fail partway through

Scenario writing guidelines:

- Use Given-When-Then format consistently
- Include concrete data in Given/When/Then statements (real
  emails, tokens, passwords)
- Add "And" statements to show complete multi-step flow
- Add "But" statements to show what does NOT happen
- Show exact error messages user sees: "Then system returns
  error 'Password must be at least 8 characters'"
- Not vague: "Then validation fails"

Quality Standards:

Original codex ~100-300 lines → Expanded codex 800-1200+
lines Original 10-15 rules → 40-55+ categorized rules  
Original 3-5 scenarios → 25-35+ comprehensive scenarios Add
3-5 mermaid diagrams where original has none Add 5-10+
detailed tables for all data structures

**Additional sections to include:**

- Security Considerations section (dedicated, detailed
  explanation in business terms)
- Implementation Notes section (file locations, key
  functions, configuration - still in plain language)
- Summary section at end (recap key points, user
  recommendations, system behavior overview)
- Known Limitations section (what system doesn't do, future
  enhancements)
- Troubleshooting section (common issues users face, how to
  resolve)

Tone: Professional but approachable. Write as if explaining
to a smart product manager who doesn't code but needs to
make decisions about features, understand constraints, and
communicate with customers.

Work Management:

Use the manage_todo_list tool to break down work into 6
manageable tasks:

1. Research implementation (read code files, document
   findings)
2. Expand Rules section (40-55+ categorized rules)
3. Create Mermaid diagrams (3-5 diagrams)
4. Create detailed tables (5-10+ tables)
5. Write Gherkin scenarios (25-35+ scenarios)
6. Review and finalize (quality check, ensure 800-1200+
   lines, add Summary/Security/Troubleshooting sections)

Mark each task as in-progress when starting, completed when
done. This prevents response length limits and ensures
thorough coverage. Work through tasks sequentially, not all
at once.

**Important reminders:**

- Replace ALL technical jargon with business language
  (MongoDB → database, bcrypt → encryption, etc.)
- Explain WHY behind every design decision in business terms
- Use concrete examples everywhere (real emails, actual
  error messages)
- Add Summary section at end recapping key behaviors
- Keep Implementation Notes but translate to plain language
- Focus on what users see and experience, not how code works

As always, remember: Codices are non-technical documents
reflecting the ground-truth reality of the code to
non-technical product people.

When I say "And, this one?": I'm presenting the next codex
file for comprehensive expansion using this exact approach.
