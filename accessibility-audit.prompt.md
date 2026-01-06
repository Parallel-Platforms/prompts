# Accessibility Audit Prompt

> Audit web or mobile UI for accessibility compliance and
> usability.

---

## Prompt

Perform an accessibility audit on the code/component I
provide. Identify issues and provide fixes following WCAG
2.1 guidelines.

### Audit Categories

Check for issues in these areas:

#### 1. Perceivable

- **Images** — Alt text present and descriptive
- **Color contrast** — Minimum 4.5:1 for normal text, 3:1
  for large text
- **Color alone** — Information not conveyed by color only
- **Captions** — Video/audio has captions or transcripts
- **Resize** — Content readable at 200% zoom

#### 2. Operable

- **Keyboard navigation** — All interactive elements
  focusable
- **Focus visible** — Focus indicator clearly visible
- **Focus order** — Logical tab order
- **Skip links** — Skip to main content available
- **Touch targets** — Minimum 44x44px on mobile
- **Timing** — No time limits or ability to extend

#### 3. Understandable

- **Labels** — Form inputs have associated labels
- **Error messages** — Clear, specific error descriptions
- **Instructions** — Required fields and format indicated
- **Consistent navigation** — Same components, same order
- **Language** — Page language declared

#### 4. Robust

- **Valid HTML** — Proper semantics and nesting
- **ARIA usage** — ARIA used correctly when needed
- **Name, Role, Value** — Custom components properly
  identified

### Report Format

````markdown
## Accessibility Audit Summary

**Severity:** [Critical / Major / Minor issues found] **WCAG
Level:** Issues affecting [A / AA / AAA] compliance

## Critical Issues 🔴

### [Issue: Missing form labels]

**Location:** `ComponentName.tsx` line X **WCAG Criterion:**
1.3.1 Info and Relationships (Level A) **Impact:** Screen
reader users cannot identify form fields **Current code:**

```jsx
<input type='email' placeholder='Email' />
```
````

**Fixed code:**

```jsx
<label htmlFor="email">Email</label>
<input id="email" type="email" placeholder="Email" />
```

## Major Issues 🟡

[Same format]

## Minor Issues 🔵

[Same format]

## Passed Checks ✅

- [List what's done correctly]

```

### Common Issues Checklist

#### HTML Structure
- [ ] Heading hierarchy (h1 → h2 → h3, no skipping)
- [ ] Landmark regions (main, nav, header, footer)
- [ ] Lists for list content (ul, ol, dl)
- [ ] Tables have headers and captions
- [ ] Language attribute on html element

#### Interactive Elements
- [ ] Buttons for actions, links for navigation
- [ ] Button/link text is descriptive (not "click here")
- [ ] Custom controls have ARIA roles
- [ ] Disabled states communicated accessibly
- [ ] Loading states announced

#### Forms
- [ ] Every input has a label
- [ ] Required fields indicated (not just by color)
- [ ] Error messages associated with fields
- [ ] Autocomplete attributes where appropriate
- [ ] Fieldset/legend for related inputs

#### Images and Media
- [ ] Decorative images have empty alt=""
- [ ] Informative images have descriptive alt
- [ ] Complex images have extended descriptions
- [ ] Icons have accessible names
- [ ] SVGs have title or aria-label

#### Focus and Keyboard
- [ ] No keyboard traps
- [ ] Modal focus trapped correctly
- [ ] Focus returned after modal close
- [ ] Custom components keyboard accessible
- [ ] No positive tabindex values

### Testing Recommendations

After fixes, verify with:

1. **Keyboard only** — Navigate without mouse
2. **Screen reader** — Test with VoiceOver/NVDA
3. **Zoom to 200%** — Verify content reflows
4. **High contrast mode** — Verify visibility
5. **Automated tools** — axe, Lighthouse, WAVE
```
