---
name: frontend-design
description: |
  Build distinctive, production-grade frontend interfaces with exceptional design quality. Use this skill for ANY frontend request - landing pages, marketing sites, web apps, dashboards, Claude artifacts, React components, HTML/CSS layouts, or UI redesigns. Trigger whenever the user asks to build, design, redesign, style, or beautify any web interface. This skill ensures outputs are brief-faithful, mobile-responsive, visually distinctive, and never generic AI slop.
---

# Frontend Design Skill

Build frontend interfaces that are brief-faithful, visually distinctive, fully responsive, and production-ready. This skill covers landing pages, marketing sites, web apps, dashboards, and Claude artifacts across HTML/CSS/JS, React, Vue, and other frameworks.

---

## Step 1: Read the Brief Before Writing a Single Line of Code

This is the most important step. Generic, off-brief output almost always happens because the brief wasn't fully parsed before building started.

Before touching code, extract and confirm these from the user's request:

**Purpose & Audience**
- What is this for? (marketing, internal tool, product UI, portfolio, etc.)
- Who uses it? (potential clients, internal team, general public, specific persona)
- What action should a visitor take? (sign up, contact, understand something, use a tool)

**Content & Structure**
- What sections/pages are required?
- Is there existing copy, or does it need to be written?
- Are there specific elements that MUST be included? (forms, CTAs, pricing tables, etc.)

**Technical Constraints**
- Framework preference? (plain HTML, React, Vue — default to what's most appropriate for the context)
- Will this be deployed or is it a prototype/artifact?
- Any integrations needed? (forms, analytics, auth)
- Are there existing brand assets? (colors, fonts, logo, style guide)

**If anything is ambiguous, ask one targeted clarifying question before proceeding.** Never assume and build the wrong thing.

---

## Step 2: Choose an Aesthetic Direction

After fully understanding the brief, commit to a clear aesthetic direction. The direction must be appropriate to the context — not just visually interesting in isolation.

### Matching Aesthetic to Context

| Use Case | Strong Aesthetic Directions |
|---|---|
| B2B SaaS / consulting | Sharp minimal, editorial dark, structured professional |
| Agency / creative studio | Bold typographic, maximalist, editorial magazine |
| Consumer product / startup | Friendly modern, playful structured, warm editorial |
| Internal tool / dashboard | Functional clarity, data-dense minimal, utility-first |
| Portfolio / personal brand | Conceptual, distinctive, identity-driven |
| E-commerce / marketing | Conversion-focused, bold CTA hierarchy, clean scannable |

### Aesthetic Palette (pick one and commit fully)

- **Sharp Minimal** — high contrast, generous whitespace, razor-thin details, monochrome base with one accent
- **Editorial Dark** — dark backgrounds, strong typographic hierarchy, subtle textures, premium feel
- **Structured Professional** — clear grid, confident type scale, restrained color, no decorative noise
- **Bold Typographic** — type as the hero, oversized headlines, tight tracking, type-driven layout
- **Warm Editorial** — earthy or cream tones, serif type, organic shapes, cultured feel
- **Functional Utility** — dense but organized, monospace accents, data-first, developer-adjacent
- **Playful Structured** — friendly shapes, saturated but not garish colors, round corners, energetic but not chaotic
- **Maximalist** — layered, textured, abundant — everything earns its complexity

**Rule**: Pick a direction that serves the brief first, your aesthetic preferences second. Then execute it without hedging.

---

## Step 3: Typography System

Typography is the fastest way to go from generic to distinctive.

### Font Selection Rules
- Never default to Inter, Roboto, Arial, or system fonts unless there's a specific reason
- Always pair a **display font** (headlines, hero text) with a **body font** (readable at paragraph scale)
- Use Google Fonts or system font stacks that are available without a build step
- Commit to a **type scale** — set it in CSS variables and don't deviate

### Strong Pairing Examples
- `Playfair Display` + `Source Serif 4` → editorial, refined
- `Bebas Neue` + `DM Sans` → bold, modern, impactful
- `Cormorant Garamond` + `Karla` → elegant, cultured
- `Space Mono` + `Inter` → technical, developer-adjacent (Inter OK here as body)
- `Syne` + `Manrope` → contemporary, geometric
- `Libre Baskerville` + `Lato` → trustworthy, professional
- `Clash Display` + `Cabinet Grotesk` → fresh, startup-adjacent

**Size scale** (set as CSS variables):
```css
--text-xs: 0.75rem;
--text-sm: 0.875rem;
--text-base: 1rem;
--text-lg: 1.125rem;
--text-xl: 1.25rem;
--text-2xl: 1.5rem;
--text-3xl: 1.875rem;
--text-4xl: 2.25rem;
--text-5xl: 3rem;
--text-6xl: 3.75rem;
```

---

## Step 4: Color System

Set ALL colors as CSS variables at the top of the stylesheet. Never hardcode hex values inline.

### Minimum Color Set
```css
:root {
  --color-bg: ;          /* primary background */
  --color-bg-alt: ;      /* secondary background / cards */
  --color-surface: ;     /* elevated surfaces */
  --color-border: ;      /* borders / dividers */
  --color-text-primary: ;
  --color-text-secondary: ;
  --color-text-muted: ;
  --color-accent: ;      /* primary CTA / highlight */
  --color-accent-hover: ;
}
```

### Color Direction Rules
- Dominant neutral base + one strong accent outperforms multi-color palettes every time
- Dark themes: use near-black (not pure #000000) — try #0A0A0A, #0F0F0F, #111111, #141414
- Light themes: use off-white — try #FAFAFA, #F8F6F1, #F5F4F0 instead of pure #FFFFFF
- Accent colors should be decisive — not pastel, not muddy
- Test contrast ratios mentally: body text must be readable, always

---

## Step 5: Responsive Design (Non-Negotiable)

Every output must be fully responsive. This is not optional.

### Mobile-First Approach
Always write base styles for mobile, then use `min-width` media queries to scale up:
```css
/* Mobile base */
.hero { padding: 3rem 1.25rem; }

/* Tablet */
@media (min-width: 768px) {
  .hero { padding: 5rem 2rem; }
}

/* Desktop */
@media (min-width: 1024px) {
  .hero { padding: 8rem 4rem; }
}
```

### Breakpoint Set
```
sm: 640px | md: 768px | lg: 1024px | xl: 1280px | 2xl: 1536px
```

### Responsive Checklist (verify before finalizing)
- [ ] Navigation collapses to hamburger or stacked on mobile
- [ ] Typography scales down gracefully — hero text doesn't overflow
- [ ] Images and media have max-width: 100%
- [ ] No horizontal scroll at any breakpoint
- [ ] Touch targets (buttons, links) are minimum 44x44px on mobile
- [ ] Multi-column grids collapse to single column on small screens
- [ ] Forms are full-width and easy to interact with on mobile
- [ ] Hero sections don't have fixed heights that break on small screens

---

## Step 6: Layout & Composition

### Grid System
Use CSS Grid for page-level layout, Flexbox for component-level alignment.

```css
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1.25rem;
}
@media (min-width: 768px) {
  .container { padding: 0 2rem; }
}
```

### Spatial Hierarchy Rules
- Section spacing: generous vertical padding between sections (4rem–10rem depending on density)
- Asymmetry over symmetry: offset elements, staggered grids, diagonal flow feel designed
- Negative space: let elements breathe — crowded layouts feel cheap
- Visual weight: every section should have one clear focal point

### Anti-Patterns to Avoid
- Centered everything (reads as template, not designed)
- Equal spacing everywhere (no rhythm)
- All elements same size (no hierarchy)
- Flat, shadowless cards on white backgrounds
- Stock-looking placeholder content

---

## Step 7: Motion & Interaction

Use motion purposefully — to reinforce hierarchy and guide attention, not as decoration.

### What to Animate (High ROI)
- **Page load**: Staggered fade-in of hero elements
- **Scroll reveals**: Sections entering from below as user scrolls
- **Hover states**: Buttons, cards, links — should always respond to hover
- **CTA buttons**: Subtle scale + shadow shift on hover

### CSS-Only Animation Patterns
```css
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(20px); }
  to   { opacity: 1; transform: translateY(0); }
}
.animate-in { animation: fadeUp 0.6s ease forwards; }
.delay-1    { animation-delay: 0.1s; }
.delay-2    { animation-delay: 0.2s; }
.delay-3    { animation-delay: 0.3s; }

.card:hover { transform: translateY(-4px); box-shadow: 0 12px 40px rgba(0,0,0,0.15); transition: all 0.25s ease; }
```

### Motion Rules
- Entrance animations: 0.4s–0.7s, ease or ease-out
- Hover transitions: 0.15s–0.25s, ease
- Never animate more than 3–4 things simultaneously
- Always respect reduced motion preference:

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation-duration: 0.01ms !important; transition-duration: 0.01ms !important; }
}
```

---

## Step 8: Component Patterns

### Buttons — Always Define a Hierarchy
```css
.btn { padding: 0.75rem 1.5rem; border-radius: 6px; font-weight: 600; cursor: pointer; transition: all 0.2s ease; display: inline-flex; align-items: center; gap: 0.5rem; }
.btn-primary   { background: var(--color-accent); color: var(--color-bg); }
.btn-secondary { background: transparent; border: 1px solid var(--color-border); color: var(--color-text-primary); }
.btn-ghost     { background: transparent; color: var(--color-accent); }
```

### Navigation
- Desktop: horizontal nav with clear active states
- Mobile: hamburger that opens full-width overlay or slide-in drawer
- Always include smooth scroll to anchor links on single-page layouts

### Cards
- Consistent padding (1.5rem–2rem)
- Subtle border OR shadow — not both unless intentional
- Clear content hierarchy within: label → heading → body → action

### Forms
- Full-width inputs on mobile
- Visible focus states (outline or border color change)
- Inline validation messaging
- Submit button is clearly the primary action

---

## Step 9: Code Quality Standards

### HTML
- Semantic elements: header, main, section, article, footer, nav
- All images have descriptive alt attributes
- Form inputs have associated label elements
- Logical heading hierarchy: one h1, then h2, h3

### CSS
- All design tokens as CSS variables
- Classes named for role, not appearance (.hero-cta not .blue-button)
- No inline styles except dynamic values
- Logical order: reset → variables → base → layout → components → utilities

### JavaScript (when needed)
- Vanilla JS preferred for simple interactions
- No console.log left in final output
- Comments only where logic is non-obvious

### Single-File Artifacts (Claude chat)
Consolidate in this order: HTML structure → `<style>` in `<head>` → `<script>` before `</body>`. Import fonts via Google Fonts link tag.

---

## Step 10: Final QA Before Delivering

**Brief Faithfulness**
- [ ] Every required section/element from the brief is present
- [ ] Copy reflects the actual purpose — no Lorem Ipsum unless it's a wireframe
- [ ] CTAs match the stated conversion goal

**Visual Quality**
- [ ] Aesthetic direction is clear and consistent throughout
- [ ] Typography creates hierarchy — not all text the same size/weight
- [ ] Color system is consistent — CSS variables used throughout
- [ ] No section looks weaker than the others

**Responsive**
- [ ] Layout works at 375px (mobile), 768px (tablet), 1280px (desktop)
- [ ] No overflow, no broken grids, no overlapping text at any width
- [ ] Touch targets are large enough on mobile

**Code**
- [ ] No syntax errors
- [ ] External fonts/libraries load from CDN (Google Fonts, cdnjs, unpkg)
- [ ] No placeholder logic or TODO comments left in output

---

## Output Format by Context

| Context | Format |
|---|---|
| Claude artifact | Single HTML file: style in head, script before /body, Google Fonts via link tag |
| Claude artifact (React) | JSX with Tailwind utilities, default export, no required props |
| Deployed site (plain) | Multi-file: index.html + styles/ + scripts/ |
| Deployed site (React) | Vite recommended, component-per-section, CSS modules or Tailwind |
| Wireframe/prototype | Clearly labeled, placeholder content OK but layout must be brief-faithful |

---

## The Rule That Overrides Everything

**Serve the brief first.** A restrained, perfectly executed professional layout that hits every brief requirement is always better than a visually adventurous design that misses the point. When in doubt: re-read the brief, then build.
