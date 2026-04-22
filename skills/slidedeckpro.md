---
name: slide-deck-pro
description: Transforms natural language into structured, presentation-ready slide decks. Use this skill whenever the user wants to create a presentation, pitch deck, slide deck, or slides from a topic, idea, brief, or document — even if they don't say "slide deck" explicitly. Trigger on phrases like "make slides about", "build a deck on", "create a presentation for", "turn this into slides", or "I need to present X". Always use this skill before generating any slide content to ensure consistent structure, Rule of 6 formatting, visual suggestions, and speaker notes.
---

# Slide Deck Pro

Transforms any topic, brief, or document into a fully structured, presentation-ready slide deck.

---

## Core Rules

### Rule of 6
- Max **6 bullet points** per slide
- Max **6 words** per bullet
- Every word earns its place — no filler

### Required Output Per Slide
1. **Slide Title** — clear and punchy
2. **Bullet Points** — follow Rule of 6 strictly
3. **Visual Suggestion** — describe an icon, image, or graphic that fits the slide
4. **Speaker's Script** — a short paragraph (3–5 sentences) the presenter can speak naturally from

---

## Default Slide Structure

Follow this sequence unless the user specifies otherwise:

| # | Slide Type | Purpose |
|---|------------|---------|
| 1 | **Title** | Hook the audience. State the topic and presenter. |
| 2 | **Agenda** | Outline what's coming. Set expectations. |
| 3 | **Problem** | Define the pain point or challenge clearly. |
| 4 | **Solution** | Present the answer, approach, or idea. |
| 5 | **Data / Proof** | Back it up with stats, examples, or evidence. |
| 6 | **Conclusion** | Summarize, call to action, or closing thought. |

> For longer decks, expand between Problem–Solution and Data/Proof with supporting slides (e.g., How It Works, Case Study, Team, Roadmap). Keep the opening and closing anchored to this structure.

---

## Output Format (per slide)

```
---
### Slide [N]: [Title]

**Bullets:**
- [Point 1 — max 6 words]
- [Point 2 — max 6 words]
- [Point 3 — max 6 words]
...

**Visual:** [Describe a specific image, icon, or graphic — be concrete]

**Speaker's Script:**
[3–5 sentences. Natural, confident, conversational tone. Expands on the bullets without reading them.]
---
```

---

## Tone & Style Guidelines

- Match the deck's purpose: professional for business, energetic for sports/fitness, academic for research
- Bullets should be **statements or fragments**, not full sentences
- Speaker's Script should sound like a **real person talking**, not an essay
- Visuals should be **specific** ("a split image of a cluttered desk vs. a clean desk") not vague ("a relevant image")

---

## Behavior on Input

| Input type | Claude's action |
|------------|-----------------|
| Topic only (e.g., "nutrition for athletes") | Generate full deck using default structure |
| Existing outline | Reformat into slide-deck-pro format |
| Document / notes | Distill into slides — condense, don't copy |
| Specific slide count requested | Distribute structure across that count |
| No structure preference stated | Default 6-slide structure |

---

## Example Output

```
---
### Slide 1: Title

**Bullets:**
- Nutrition for Peak Athletic Performance
- Presented by [Name]
- [Organization / Class / Event]

**Visual:** A dynamic athlete mid-sprint on a track, with colorful food icons (protein, carbs, water) floating alongside.

**Speaker's Script:**
Today we're talking about something every athlete deals with but not everyone gets right — nutrition. What you put in your body directly affects how fast you recover, how hard you train, and how well you compete. Whether you're a weekend warrior or training daily, this applies to you. Let's break it down simply and practically.
---
```
