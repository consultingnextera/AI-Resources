# Design to Code Handoff

Use this to translate design specs into a developer-ready component architecture. The handoff document bridges design intent and engineering requirements, reducing rework and ensuring visual fidelity carries through to production.

---

**Two ways to use this:**
- **Paste the whole file into an LLM** — it will interview you and fill out the template at the bottom
- **Copy just the template** — scroll to the bottom and fill it in yourself

---

## LLM Instructions

Act as a design-to-engineering liaison. Interview the designer about their component layout, states, and interactions, then structure a handoff document with component specs, props, and implementation notes.

**SECTION 1 — Design Overview**

- What screen or component are you handing off? What's its purpose in the product?
- What design system or component library are you using? (Material Design, custom, etc.)
- Are there existing components you're building on, or is this a new design?
- What devices or breakpoints does this need to support? (mobile, tablet, desktop)

**SECTION 2 — Component Breakdown**

- What are the main components on this screen? (header, navigation, cards, forms, etc.)
- For each component, what are the visual states? (default, hover, active, disabled, loading, error)
- Are there interactions or animations? (transitions, hover effects, modals, etc.)
- Do any components have dynamic content? (text length variations, lists, conditional display)

**SECTION 3 — Design Tokens & Styling**

- What colors are used? (primary, secondary, neutral, semantic colors)
- What typography is used? (font families, sizes, weights, line heights)
- What spacing and sizing system? (8px grid, rem-based, etc.)
- Are there shadows, borders, or other visual effects?

**SECTION 4 — Data & Content**

- What data does each component display or accept?
- Are there different content scenarios? (short text, long text, empty state, error state)
- How should components handle overflow or truncation?
- Are there any content limits or validation rules?

**SECTION 5 — Responsive & Edge Cases**

- How does the design adapt to different screen sizes?
- What happens when text wraps or content expands?
- How should components behave on touch devices vs. desktop?
- What accessibility considerations are there? (focus states, semantic HTML, labels)

Create a component spec with layouts, props, states, and implementation notes for each major component.

---

## Template

Copy the block below — paste it into a new file and fill it in.

````markdown
# Design Handoff: [SCREEN / COMPONENT NAME]

**Date:** [DATE] | **Designer:** [NAME] | **Intended for:** [DEVELOPER / TEAM]

## Design Overview
**Purpose:** [WHAT THIS COMPONENT/SCREEN DOES]
**Context:** [WHERE IT APPEARS IN THE PRODUCT]
**Screen sizes:** [MOBILE / TABLET / DESKTOP] — [BREAKPOINTS: e.g., 320px, 768px, 1200px]

## Component Inventory

| Component | Purpose | States | Props | Notes |
|-----------|---------|--------|-------|-------|
| [NAME] | [WHAT IT DOES] | default / hover / active / disabled / loading / error | [PROPS] | [NOTES] |
| [NAME] | [WHAT IT DOES] | default / hover / active / disabled / loading / error | [PROPS] | [NOTES] |

## Component Specifications

### Component 1: [NAME]
**Purpose:** [WHAT IT DOES]
**Layout:** [DESCRIPTION of structure]

**Visual States:**
- Default: [APPEARANCE]
- Hover: [APPEARANCE]
- Active/Focused: [APPEARANCE]
- Disabled: [APPEARANCE]
- Loading: [APPEARANCE]
- Error: [APPEARANCE]

**Props & Content:**
- Prop: `label` (string) — [DESCRIPTION]
- Prop: `size` (small | medium | large) — [DESCRIPTION]
- Prop: `disabled` (boolean) — [DESCRIPTION]

**Responsive Behavior:**
- Desktop (1200px+): [LAYOUT]
- Tablet (768px): [LAYOUT]
- Mobile (320px): [LAYOUT]

**Interactions:**
- On click: [BEHAVIOR]
- On focus: [BEHAVIOR]
- Animations: [DURATION, easing, when triggered]

---

## Design Tokens
| Token | Value | Usage |
|-------|-------|-------|
| Primary color | [HEX/RGB] | [WHERE USED] |
| Font family | [FAMILY] | [WHERE USED] |
| Spacing unit | [SIZE] | [WHERE USED] |
| Border radius | [SIZE] | [WHERE USED] |

## Edge Cases & Fallbacks
- Long text handling: [TRUNCATE / WRAP / OVERFLOW]
- Empty state: [DISPLAY]
- Error state: [DISPLAY]
- Loading state: [DISPLAY]
- RTL support: [YES / NO]

## Accessibility Notes
- Focus indicators: [STYLED HOW]
- Keyboard navigation: [SUPPORTED FOR]
- ARIA labels: [REQUIRED FOR]
- Color contrast: [VERIFIED: YES / NO]
````

---

> Adapted from [awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts) (CC0) | **consulting.nextera@gmail.com** | [nexteraconsult.com/ai](https://nexteraconsult.com/ai)
