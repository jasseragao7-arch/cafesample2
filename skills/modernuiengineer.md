---
name: modern-ui-designer
description: >
  Enforces a production-grade design system to prevent generic "AI slop" aesthetics in UI output.
  Use this skill whenever the user asks to build, design, or style any UI — including web components,
  landing pages, dashboards, HTML artifacts, React components, or any visual interface. Also trigger
  when the user says "make it look good", "clean up the design", "style this", "modern UI", or
  "professional interface". If there's any UI or frontend work involved, this skill should be active.
  It ensures bold typography, purposeful spacing, high-contrast palettes, and micro-interactions
  that distinguish the output from low-effort AI-generated designs.
---

# Modern UI Designer

A design system enforcer that prevents generic AI aesthetics and produces production-grade interfaces.

---

## Philosophy

**Anti-patterns to avoid:**
- Purple/blue gradient backgrounds ("AI slop" signature)
- Rounded cards floating on gray gradients
- Overuse of shadow and glow effects
- Pastel color schemes with no contrast
- Random icon usage without purpose

**Design principles to follow:**
- Bold, expressive typography as the primary visual element
- Purposeful negative space — whitespace is not emptiness, it's structure
- High-contrast, minimal palettes (Zinc, Slate, Stone, or brand-defined)
- Every element earns its place — no decoration without function

---

## Step 1: Write the Aesthetic Goal (Required)

**Before writing any code**, output a short paragraph (3–5 sentences) describing:
- The visual mood and energy of the interface
- The palette and typography choices and why they were chosen
- The key interaction or layout decision that makes this stand out

Label it clearly:

> **🎨 Aesthetic Goal:** [Your paragraph here]

Do not skip this step. It anchors all design decisions that follow.

---

## Design System

### Typography
- **Primary font**: `Inter`, `system-ui`, `-apple-system`, `sans-serif`
- **Scale**: Use a strict type scale — 12 / 14 / 16 / 20 / 24 / 32 / 48 / 64px
- **Weight**: Use 400 (body), 600 (label/subheading), 700–800 (headline)
- **Line height**: 1.2 for headings, 1.6 for body text

### Color Palette
Default to **Zinc** or **Slate** unless the user specifies a brand color:

```css
/* Zinc palette (preferred dark-capable) */
--color-950: #09090b;
--color-900: #18181b;
--color-800: #27272a;
--color-700: #3f3f46;
--color-500: #71717a;
--color-300: #d4d4d8;
--color-100: #f4f4f5;
--color-50:  #fafafa;

/* Accent — one bold color only */
--accent: #f97316;       /* Orange — energetic, sporty */
/* or */
--accent: #3b82f6;       /* Blue — clean, professional */
/* or */
--accent: #10b981;       /* Emerald — growth, health */
```

**Rules:**
- Max 2 colors: a neutral base + one accent
- Never use gradients as backgrounds. Gradients allowed only on isolated elements (buttons, badges)
- Text must meet WCAG AA contrast (4.5:1 minimum)

### Spacing (8px Grid)
All spacing values must be multiples of 8:

| Token | Value |
|-------|-------|
| `--space-1` | 8px |
| `--space-2` | 16px |
| `--space-3` | 24px |
| `--space-4` | 32px |
| `--space-6` | 48px |
| `--space-8` | 64px |

No arbitrary values like `padding: 13px` or `margin: 7px`.

### Border Radius
- **Sharp** (default): `4px` — confident, structured
- **Soft** (cards/inputs): `8px`
- **Pill** (tags/badges): `9999px`
- Avoid `border-radius: 16px` or higher on layout containers — it's a key "AI slop" marker

---

## Component Patterns

### Buttons
```css
.btn-primary {
  background: var(--accent);
  color: white;
  font-weight: 600;
  font-size: 14px;
  padding: 10px 24px;
  border-radius: 4px;
  border: none;
  cursor: pointer;
  transition: all 0.2s ease;
}
.btn-primary:hover {
  opacity: 0.88;
  transform: translateY(-1px);
}
.btn-primary:active {
  transform: translateY(0);
  opacity: 1;
}
```

### Cards
```css
.card {
  background: var(--color-900);
  border: 1px solid var(--color-800);
  border-radius: 8px;
  padding: var(--space-3);
  /* No box-shadow unless used sparingly for depth */
}
```

### Inputs
```css
input, textarea, select {
  background: var(--color-950);
  border: 1px solid var(--color-700);
  border-radius: 4px;
  padding: 10px 14px;
  font-size: 14px;
  color: var(--color-50);
  transition: border-color 0.2s ease;
}
input:focus {
  outline: none;
  border-color: var(--accent);
}
```

---

## Micro-Interactions (Required)

Every interactive element must have a transition. Use:
```css
transition: all 0.2s ease;
```

Standard micro-interactions:
- **Hover on clickable**: subtle opacity drop or `translateY(-1px)`
- **Focus on inputs**: accent border color
- **Active/pressed**: `transform: scale(0.98)` or `translateY(0)` reset
- **Loading state**: opacity pulse or skeleton shimmer, not a spinner

---

## Mobile-First Layout

Always start with mobile styles, then use `min-width` breakpoints:
```css
/* Mobile default */
.container { padding: 0 var(--space-2); }

/* Tablet */
@media (min-width: 640px) { ... }

/* Desktop */
@media (min-width: 1024px) { ... }
```

---

## Quality Checklist (Run before finalizing)

- [ ] Aesthetic Goal written and visible in output
- [ ] No purple/blue gradient backgrounds
- [ ] Typography uses Inter/system-ui with defined scale
- [ ] All spacing on 8px grid
- [ ] Max 2 colors in palette
- [ ] Border radius ≤ 8px on containers
- [ ] Every interactive element has a `transition`
- [ ] Mobile-first layout structure
- [ ] WCAG AA contrast verified (mentally or via code)
- [ ] No decorative elements without purpose
