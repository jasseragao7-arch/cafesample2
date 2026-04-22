---
name: artifact-engineer
description: Builds interactive dashboards, calculators, tools, and mini web-apps as single-file artifacts using React (JSX) or p5.js. Use this skill when the user asks to build something interactive — dashboards, data visualizers, calculators, simulators, trackers, games, generative art, or any tool with real-time inputs and outputs. Trigger when the user says things like "build me a tool", "make an interactive", "create a dashboard", "visualize this data", "make a calculator for", "I want something I can play with", or "build an app that". Always use for anything that benefits from live input → output feedback. Prefer React for UI-heavy apps and data dashboards; prefer p5.js for generative, canvas-based, or animation-driven work.
---

# Artifact Engineer

Builds polished, interactive single-file artifacts — React dashboards, p5.js sketches, calculators, and mini web-apps — with real-time responsiveness and a clean, consistent aesthetic.

---

## Core Rules

1. **Single file only.** All HTML, CSS, and JS go in one artifact block. No external files, no separate stylesheets.
2. **Real-time by default.** Inputs must update outputs instantly — no submit buttons unless the use case genuinely requires a confirmation step.
3. **Never use localStorage or sessionStorage.** All state lives in React state or JS variables. These APIs are not supported in Claude artifacts.
4. **No `<form>` tags in React.** Use `onClick`, `onChange`, `onInput` handlers instead.
5. **Default export required.** Every React component must have a default export with no required props (or defaults provided for all props).

---

## Aesthetic System — Claude Clean

Apply this design language consistently across all artifacts unless the user specifies otherwise.

### Color Palette (CSS Variables)
```css
:root {
  --bg:         #ffffff;
  --bg-subtle:  #f8f9fb;
  --bg-card:    #ffffff;
  --border:     #e5e7eb;
  --border-focus: #6366f1;
  --text-primary:   #111827;
  --text-secondary: #6b7280;
  --text-muted:     #9ca3af;
  --accent:         #6366f1;   /* indigo-500 */
  --accent-light:   #eef2ff;   /* indigo-50  */
  --accent-hover:   #4f46e5;   /* indigo-600 */
  --success:  #10b981;
  --warning:  #f59e0b;
  --danger:   #ef4444;
  --shadow-sm: 0 1px 3px rgba(0,0,0,0.06), 0 1px 2px rgba(0,0,0,0.04);
  --shadow-md: 0 4px 12px rgba(0,0,0,0.08), 0 2px 4px rgba(0,0,0,0.04);
  --radius-sm: 8px;
  --radius-md: 12px;
  --radius-lg: 16px;
}
```

### Typography
- **Primary font**: `'Inter', system-ui, sans-serif` (load from Google Fonts if needed)
- **Monospace / data**: `'JetBrains Mono', 'Fira Code', monospace`
- Headings: `font-weight: 600–700`, tight letter-spacing (`-0.02em`)
- Body: `font-size: 14–15px`, `line-height: 1.6`
- Labels: `font-size: 11–12px`, `letter-spacing: 0.05em`, `text-transform: uppercase`, `color: var(--text-muted)`

### Component Patterns

**Cards**
```css
.card {
  background: var(--bg-card);
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  box-shadow: var(--shadow-sm);
  padding: 20px 24px;
}
```

**Inputs**
```css
input, select, textarea {
  border: 1.5px solid var(--border);
  border-radius: var(--radius-sm);
  padding: 8px 12px;
  font-size: 14px;
  transition: border-color 0.15s;
  outline: none;
}
input:focus {
  border-color: var(--border-focus);
  box-shadow: 0 0 0 3px rgba(99,102,241,0.12);
}
```

**Buttons**
```css
.btn-primary {
  background: var(--accent);
  color: white;
  border: none;
  border-radius: var(--radius-sm);
  padding: 9px 18px;
  font-weight: 500;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
}
.btn-primary:hover { background: var(--accent-hover); }
.btn-primary:active { transform: scale(0.98); }
```

**Stat / KPI tiles**
```
[LABEL]
[Large value]
[Trend or sub-label]
```
Use `--accent-light` background with `--accent` colored value text for emphasis tiles.

---

## Framework Selection

| Use React (JSX) when... | Use p5.js when... |
|---|---|
| UI has forms, tables, lists, or multiple views | Output is canvas-based or generative |
| Data needs to be filtered, sorted, or computed | Real-time animation or physics involved |
| Dashboard with multiple metric cards | Drawing, particles, simulations, visual art |
| App has multiple interaction states | Audio visualization |

---

## React Artifacts — Requirements

```jsx
import { useState, useEffect, useCallback } from "react";

// Always default export, no required props
export default function MyApp() {
  const [value, setValue] = useState(0);
  // ...
  return <div style={styles.container}>...</div>;
}

// Inline styles OR Tailwind utility classes (core only)
const styles = {
  container: {
    fontFamily: "'Inter', system-ui, sans-serif",
    background: "#f8f9fb",
    minHeight: "100vh",
    padding: "24px",
  }
};
```

**Available libraries** (import directly):
- `recharts` — charts and data visualization
- `lucide-react@0.383.0` — icons
- `lodash` — data utilities
- `mathjs` — math expressions and unit conversions
- `d3` — advanced data viz and layout
- `shadcn/ui` — pre-built UI components (note to user if used)

---

## p5.js Artifacts — Requirements

Use HTML artifact mode. Load p5.js from CDN:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.9.0/p5.min.js"></script>
```

Structure:
```html
<!DOCTYPE html>... <!-- NOT needed in artifact — just inline HTML -->
<div id="sketch-container"></div>
<script>
new p5(function(p) {
  p.setup = function() {
    let canvas = p.createCanvas(p.windowWidth, p.windowHeight);
    canvas.parent('sketch-container');
  };
  p.draw = function() { /* ... */ };
  p.windowResized = function() { p.resizeCanvas(p.windowWidth, p.windowHeight); };
});
</script>
```

Always handle `windowResized` for responsive canvas. Apply the Claude Clean palette via hex values (convert CSS vars to static values for p5 contexts).

---

## Real-Time Interaction Checklist

Before finalizing any artifact, verify:

- [ ] All sliders, inputs, and toggles update the output on every change (no stale state)
- [ ] No submit/calculate button unless truly needed (e.g., API call, expensive computation)
- [ ] Number inputs have sensible min/max/step attributes
- [ ] Edge cases handled: zero values, empty inputs, division by zero, negative numbers
- [ ] Loading or empty states are shown when data is absent
- [ ] Hover states on interactive elements give visual feedback

---

## Output Format

Every artifact should open with a compact header section:

```
[App Name]  ·  [One-line description]
```

Then the interactive content. No splash screens, no loading animations on initial render unless data is being fetched.

For dashboards specifically, structure the layout as:
1. Header row (title + any global controls/filters)
2. KPI tiles row
3. Charts / main content area
4. Detail table or secondary info (if needed)

---

## Quality Bar

A finished artifact must:
- Work correctly on first render with no broken layout
- Have no hardcoded magic numbers without a comment explaining them
- Use consistent spacing (multiples of 4px or 8px)
- Handle at least the most obvious edge cases
- Look intentional — not like a default browser stylesheet with some color applied
