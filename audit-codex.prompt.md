Codex Enhancement Prompt

I need you to comprehensively expand codex documentation files for the Puff Club platform. These codices are plain-language business rule documents written for non-technical product owners, PMs, and stakeholders to understand ground-truth code behavior.

Your Task:
Review and dramatically expand codex files to be complete, authoritative references for all business logic, user flows, validation rules, and edge cases.

Required Structure for Each Codex:

Rules Section (40-55+ rules organized into 6-8 categories)

Group related rules under clear category headers
Use numbered lists for easy reference
Write in plain language avoiding technical jargon
Cover: core behavior, validation, permissions, state management, error handling, edge cases
Multiple Mermaid Diagrams (3-5 diagrams minimum)

Main user flow (flowchart showing complete journey)
State transitions (if applicable)
Error handling flow (decision tree)
Integration flows (data flow between components)
Use clear labels, decision points, and outcomes
Detailed Tables (5-10+ tables)

Field specifications with validation rules
State matrices showing all possible states and transitions
Error messages with conditions
Permission matrices (who can do what)
API parameters and responses
Sort/filter options
Comprehensive Gherkin Scenarios (25-35+ scenarios)

Cover happy path (5-8 scenarios)
Cover validation failures (5-8 scenarios)
Cover edge cases (5-8 scenarios)
Cover permissions/access control (3-5 scenarios)
Cover integration points (3-5 scenarios)
Use Given-When-Then format with detailed tables
Research Process:

Read the original codex file
Use semantic_search to find implementation files
Use grep_search to find specific patterns
Use read_file to study detailed implementation
Identify ALL gaps between current codex and actual code behavior
Writing Guidelines:

Non-technical language: Avoid terms like "ObjectId", "async", "Promise" - use "unique ID", "background process", "waiting for result"
Product owner perspective: Focus on user-facing behavior, business rules, data constraints
Complete coverage: Don't leave gaps - document every validation, every error state, every edge case
Examples everywhere: Use concrete examples in rules, tables, and scenarios
Visual aids: Prefer mermaid diagrams over text descriptions of flows
Quality Standards:

Original codex ~100-300 lines → Expanded codex 800-1200+ lines
Original 10-15 rules → 40-55+ categorized rules
Original 3-5 scenarios → 25-35+ comprehensive scenarios
Add 3-5 mermaid diagrams where original has none
Add 5-10+ detailed tables for all data structures
Tone:
Professional but approachable. Write as if explaining to a smart product manager who doesn't code but needs to make decisions about features, understand constraints, and communicate with customers.

Work Management:

Use the manage_todo_list tool to break down work into 6 manageable tasks:
1. Research implementation (read code files, document findings)
2. Expand Rules section (40-55+ categorized rules)
3. Create Mermaid diagrams (3-5 diagrams)
4. Create detailed tables (5-10+ tables)
5. Write Gherkin scenarios (25-35+ scenarios)
6. Review and finalize (quality check, ensure 800-1200+ lines)

Mark each task as in-progress when starting, completed when done
This prevents response length limits and ensures thorough coverage
Work through tasks sequentially, not all at once

When I say "And, this one?": I'm presenting the next codex file for comprehensive expansion using this exact approach.