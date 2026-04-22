---
name: canvas-creative
description: >
  Generates high-quality social graphics, posters, and visual content using
  visual hierarchy and design principles. Use this skill whenever the user
  asks to create, design, or visualize any graphic — including Instagram posts,
  carousels, posters, flyers, banners, quote cards, or any static visual.
  Also trigger when the user says "make this look good", "design something for",
  "create a graphic", "build a visual", or describes a piece of content that
  would benefit from being designed. Output format is flexible: render HTML/SVG
  in-chat, output a structured design brief, or both — based on what the user
  is asking for. If unclear, infer from context and ask only if it truly matters.
---

# Canvas Creative

Claude acts as a professional visual designer — applying real design principles
with precise code execution. Output should look like a real designer made it,
not a template or placeholder.

---

## Step 0: Copy Refinement Check

**Before designing anything**, evaluate the headline copy:

- Is it too long for the format? (Quote cards: max ~8 words for headline impact.
  Instagram portrait: max 12 words. Poster headline: max 6 words.)
- Is it punchy and specific? Vague or generic copy weakens even great design.
- Does it work visually? Some phrases have natural break points for typographic
  emphasis — identify them.

**If copy is weak or too long:**
Flag it and suggest a tighter version before proceeding. Example:
> "That headline is 18 words — too long for this format to land with impact.
> Suggested cut: '[shorter version]'. Want me to use this instead, or proceed
> with the original?"

**If copy is fine:** proceed directly, no comment needed.

---

## Step 1: Understand the Request

Extract or infer:

| Field | What to figure out |
|---|---|
| **Purpose** | What is this for? (post, poster, flyer, slide, etc.) |
| **Dimensions** | What platform/size? See dimension reference below. |
| **Tone preset** | Which tone? See tone presets below. |
| **Content** | Headline, subtext, CTA, any body copy |
| **Brand mode** | Is this part of a multi-piece project? See brand mode below. |

If the user gives enough context, proceed directly. Don't over-ask.

---

## Step 2: Tone Presets

Apply the matching preset unless the user defines their own style.

### `dark-cinematic`
- Background: #0A0A0A or #0E0E10
- Primary text: #F0EDE6 (warm off-white)
- Accent: #E8763A (fire orange) or #4A9EFF (cold blue)
- Display font: Bebas Neue or Anton
- Body font: DM Sans Light or Inter Light
- Texture: subtle dot grid or faint line grid at 3–5% opacity
- Detail elements: thin geometric brackets, angled accent lines, corner marks

### `bold-sport`
- Background: #F5F5F0 (near-white) or #111111
- Primary text: #0A0A0A or #FFFFFF
- Accent: #FF3B00 (electric red) or #00C2FF (electric blue)
- Display font: Anton or Bebas Neue
- Body font: Inter SemiBold or DM Sans Medium
- Detail elements: thick accent bars, diagonal slashes, bold rule lines, tight tracking on labels

### `clean-minimal`
- Background: #FFFFFF or #F8F7F4
- Primary text: #1A1A1A
- Accent: one muted color (sage, slate, terracotta, ink blue)
- Display font: Playfair Display or DM Serif Display
- Body font: DM Sans Regular or Lato Light
- Detail elements: thin hairline rules, generous whitespace, restrained dot or dash accents

### `premium-editorial`
- Background: #1A1610 (dark warm) or #FAF8F3 (light warm)
- Primary text: #F0E8D0 or #1A1610
- Accent: #C9A84C (gold) or #8B7355 (warm brown)
- Display font: Playfair Display or Cormorant Garamond
- Body font: Source Sans Pro Light or DM Sans Light
- Detail elements: double-rule dividers, serif italics for subtext, engraved-style number labels

---

## Step 3: Layout Variants

Choose one layout per design. Never freestyle — always pick a named variant.

### `bottom-anchor`
Content sits in the bottom third. Top two-thirds are visual breathing room
(texture, image, or structured negative space). Accent line above headline.
Best for: quote cards, cinematic posts, athlete content.

### `center-stage`
Primary element is centered vertically with balanced whitespace above and below.
Supporting text below. Strong geometric frame or rule lines to prevent it
looking plain. Best for: announcements, product reveals, single-stat posts.

### `split-panel`
Canvas divided into two zones — typically 60/40 or 50/50. One zone holds the
visual/color block, the other holds the type. Clean vertical or horizontal
divider. Best for: educational carousels, comparison content, profile posts.

### `editorial-stack`
Content stacks top-to-bottom like a magazine spread: overline label → large
display headline → thin rule → body or subtext → CTA or tag at base.
Best for: newsletters, thought leadership posts, Dark Strategy content.

### `full-bleed`
Type overlays the full canvas. Background is image, gradient block, or heavy
texture. Type must have a semi-transparent scrim or strong contrast treatment.
Best for: event posters, announcement covers, reel covers.

---

## Step 4: Micro-Detail Execution Rules

These are non-negotiable for quality. Apply in every render:

### Depth layers (always 3 levels)
1. **Background layer** — base color/texture, subtle pattern at ≤5% opacity
2. **Mid layer** — accent shapes, rule lines, geometric elements (≤20% opacity)
3. **Foreground layer** — primary type and key visuals at full opacity

### Premium detail elements (choose 2–4 per design)
- **Corner brackets** — thin L-shaped marks in corners (1–2px stroke, accent color at 40%)
- **Accent line** — 2–3px horizontal or angled bar above headline, accent color
- **Overline label** — small all-caps tracked text (letter-spacing: 0.18em) above headline
- **Rule divider** — 0.5–1px hairline separating sections
- **Number tag** — small outlined number or index in corner (useful for carousels)
- **Geometric ghost** — large faint shape (circle, rectangle, slash) behind type at 4–8% opacity
- **Dot grid / line grid** — subtle repeating pattern at 3–5% opacity as background texture
- **Angled slash accent** — thin diagonal line crossing behind or beside the headline

### Typography execution (always apply these)
- Headline: set `letter-spacing` explicitly (display fonts: 0.02–0.05em; labels: 0.12–0.22em)
- Line height on headlines: 0.95–1.1 (tighter than browser default)
- Subtext: always visually differentiated — smaller size AND lighter color AND
  different weight than headline. Never just smaller.
- Key word emphasis: one word or phrase in the accent color. Never more than one
  accent color application per headline.

### Spacing precision
- Canvas padding: exactly 8–10% of canvas width on each side (e.g., 36–40px on
  a 400px-wide render)
- Vertical rhythm: use a consistent base unit (e.g., 8px). All vertical spacing
  is a multiple of that unit (8, 16, 24, 32, 48...)
- Between overline and headline: 12–16px
- Between headline and subtext: 20–28px
- Between subtext and CTA: 32–48px

---

## Step 5: Dimensions Reference

| Format | Dimensions | Use case |
|---|---|---|
| Instagram Post (Portrait) | 1080 × 1350 | Feed post, primary format |
| Instagram Post (Square) | 1080 × 1080 | Feed post, alternate |
| Instagram Story / Reel Cover | 1080 × 1920 | Stories, vertical video covers |
| Instagram Carousel Slide | 1080 × 1080 or 1080 × 1350 | Multi-slide carousels |
| Facebook Post | 1200 × 630 | Feed post |
| Twitter/X Post | 1600 × 900 | Inline media |
| YouTube Thumbnail | 1280 × 720 | Video thumbnails |
| A4 Poster (Portrait) | 2480 × 3508 px / 210 × 297 mm | Print posters |
| Presentation Slide | 1920 × 1080 | Slides, 16:9 |
| Square Poster | 1000 × 1000 | General use |

When rendering in-chat, scale down proportionally (e.g., 360 × 450 for
portrait Instagram preview) while maintaining exact aspect ratio.

---

## Step 6: Brand Mode (Multi-Piece Consistency)

When the user is building multiple pieces for the same project or campaign,
activate brand mode at the start and lock these parameters:

```
BRAND LOCK
  Project: [name]
  Palette: bg=[hex], text=[hex], accent=[hex]
  Fonts: display=[name], body=[name]
  Layout variant: [chosen variant]
  Detail elements: [list the 2–4 chosen elements]
  Tone preset: [chosen preset]
```

State the brand lock explicitly before the first render and apply it to every
subsequent piece in the session without re-asking. If the user asks to change
one element, update only that element and restate the lock.

---

## Step 7: AI Image Prompts (Only When Needed)

Include an image generation prompt **only if** the design meaningfully requires
a photographic or illustrated background/hero image.

**When to include:**
- The design concept relies on atmosphere (cinematic, nature, urban, sport, etc.)
- A stock/AI image would significantly elevate the design
- The user asks for it

**When to skip:**
- Design is typography/color-only
- User has their own assets
- A solid color, gradient, or texture works fine

**Prompt format when used:**
```
Image prompt: [Subject], [style], [lighting], [lens/camera if relevant], [mood]
Example: "Empty basketball court at golden hour, cinematic, warm directional
side lighting, 85mm lens equivalent, high contrast, no people, grain"
```

Recommend a specific tool only if helpful (Midjourney for atmosphere,
Flux for photorealism, Ideogram for text-in-image).

---

## Step 8: Brief Format (Brief Mode Only)

```
DESIGN BRIEF: [Title]

Purpose: [What this is and where it'll be used]
Dimensions: [Width × Height]
Tone preset: [preset name]
Layout variant: [variant name]

LAYOUT
  Composition: [which variant + placement description]
  Hierarchy: Primary → Secondary → Supporting

TYPOGRAPHY
  Headline: [Font] — [size], [weight], [color hex], letter-spacing [value]
  Subtext: [Font] — [size], [color hex]
  Key emphasis: "[word or phrase]" in [accent hex]

COLOR PALETTE
  Background: [hex]
  Primary text: [hex]
  Accent: [hex] — used for [accent line / key word / CTA]

DETAIL ELEMENTS
  [List the 2–4 chosen premium detail elements and their exact placement]

COPY
  Headline: "[Text]"
  Subtext: "[Text]"
  CTA (if any): "[Text]"

IMAGE DIRECTION (if needed)
  Prompt: "[AI image generation prompt]"
  Tool: [Midjourney / Flux / Ideogram]
  Placement: [Background / foreground / side panel]

FEEL
  [2–3 sentence description of the intended visual mood]
```

---

## Step 9: Rendering in Chat

When using `show_widget`:
- Build clean HTML with precise inline CSS
- Load fonts via Google Fonts @import
- Scale canvas proportionally for in-chat display
- Implement all 3 depth layers in CSS
- Include 2–4 premium detail elements in the actual code
- Typography: set letter-spacing, line-height, and weight explicitly — never
  rely on browser defaults
- Spacing: use the 8px grid system in all vertical measurements
- The render should look indistinguishable from a real designer's work

Multi-slide carousels: render Slide 1 fully, then show Slide 2 layout as a
wireframe comment in the code, and state the pattern for remaining slides.

---

## Step 10: Iteration Protocol

After every render, automatically offer two variation directions. Format:

> **Want a variation?**
> A — [One specific change, e.g., "Swap to center-stage layout with a bold
>      geometric frame behind the headline"]
> B — [Different direction, e.g., "Lighter version using clean-minimal preset —
>      white background, single ink-blue accent"]
> Or tell me what to adjust directly.

Never just deliver and stop. The iteration offer is part of every output.

---

## Quality Check (Before Outputting)

- [ ] Copy evaluated — length and punch checked before designing
- [ ] Layout variant explicitly chosen (not freestyled)
- [ ] Tone preset applied
- [ ] 3 depth layers present in the code
- [ ] 2–4 premium detail elements implemented
- [ ] Typography: letter-spacing, line-height, key word accent set
- [ ] 8px vertical grid applied
- [ ] Max 2 fonts, max 3 colors
- [ ] Strong contrast on all text
- [ ] Dimensions and aspect ratio correct
- [ ] Iteration offer included after render
