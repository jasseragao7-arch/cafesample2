---
name: deep-researcher
description: Runs a structured 8-phase systematic inquiry process for comprehensive, citation-backed research reports. Use this skill whenever the user asks to research a topic in depth, investigate a subject thoroughly, produce a research report, analyze a complex question with multiple sources, or says things like "deep dive into", "comprehensive research on", "investigate", "give me a full report on", or "look into this properly". Also trigger when the user needs fact-checking across multiple conflicting sources, academic-style inquiry, or structured evidence synthesis. Always use this skill for non-trivial research tasks — even if the user just says "research X for me", this skill should activate.
---

# Deep Researcher

A systematic 8-phase research process for producing accurate, comprehensive, and well-cited reports on any topic.

---

## Core Principle

Every claim must trace back to a verifiable source. Contradictions between sources must be flagged explicitly — never silently resolved. Your job is to surface the truth, not present a tidy narrative.

---

## The 8 Phases

### Phase 1 — Define Scope
Before searching anything:
- Restate the research question in your own words to confirm understanding
- Identify the research type: factual, comparative, analytical, exploratory, or predictive
- Define what a complete answer looks like (what questions must be answered?)
- Set boundaries: what is explicitly out of scope?
- Note any known constraints (time period, geography, domain, depth required)

Output: A clear scope statement. Confirm with the user if the topic is ambiguous before proceeding.

---

### Phase 2 — Preliminary Search
Run an initial broad sweep to orient yourself:
- Use 3–5 high-level searches to map the landscape
- Identify the key entities, concepts, debates, and major sources in the space
- Note publication dates — flag if the topic is time-sensitive and recent data is sparse
- Do not draw conclusions yet. This phase is orientation only.

Output: A short internal map of the topic — key themes, major players, and what type of sources are available.

---

### Phase 3 — Source Verification
Before building on any source, evaluate it:
- **Authority**: Is the author/organization credible? What are their credentials or track record?
- **Recency**: Is the information current enough for this topic?
- **Bias check**: Does the source have a known agenda or conflict of interest?
- **Corroboration**: Can the key claim be found in at least one other independent source?

⚠️ **Red flags**: Single-source claims on contested facts, undated content on rapidly changing topics, opinion pieces presented as data.

Deprioritize or discard sources that fail this check. Note when a claim could only be found in one source.

---

### Phase 4 — Gap Analysis
After the preliminary search, identify what's missing:
- What key questions remain unanswered?
- Which parts of the topic have weak or thin source coverage?
- Are there conflicting claims that require deeper investigation?
- What additional searches are needed to fill these gaps?

Output: A gap list. Use it to drive Phase 5.

---

### Phase 5 — Deep Dive
Execute targeted searches to fill the gaps identified in Phase 4:
- Run focused queries on each gap area
- Prioritize primary sources (official reports, research papers, government data, direct statements) over secondary sources
- Look for counterarguments — actively seek perspectives that challenge the working thesis
- For contested claims: note the strongest argument on each side with its best supporting source

This is the most research-intensive phase. Do not rush it.

---

### Phase 6 — Synthesis
Now build the full picture:
- Organize findings into logical themes or sections
- Lead with what is well-established, then move to contested or uncertain areas
- Connect dots across sources — identify patterns, causes, implications
- **Flag contradictions explicitly**: when sources disagree on facts, do not pick a side without justification. Use this format:

> ⚠️ **Conflicting Data**: [Source A] states X, while [Source B] states Y. Possible reasons: [explain]. Most likely accurate: [your assessment if one is clearly more credible, or "unclear" if not].

- Keep the narrative honest — do not overstate certainty where it doesn't exist

---

### Phase 7 — Citation
Before finalizing, audit every factual claim in the report:
- Every specific fact, statistic, or assertion must have a citation
- Use inline citations: (Source Name, Year) or hyperlinked title
- Group all sources at the end under **References**
- Flag any claims that could not be sourced: mark them as `[Unverified]`
- Remove or reframe any claim that relies solely on a low-credibility source

---

### Phase 8 — Executive Summary
Write a tight summary at the top of the report:
- 3–5 sentences max for simple topics; up to 10 for complex ones
- Lead with the most important finding
- Include one sentence on confidence level: how strong is the evidence overall?
- Note any major unresolved contradictions or gaps

---

## Output Format

Structure the final report as:

```
## Executive Summary
[Phase 8 output]

## [Section 1 — based on synthesis themes]
...

## [Section N]
...

## Unresolved Contradictions / Gaps
[Explicit list if any exist]

## References
[All sources used]
```

---

## Integrity Rules

1. **Never fabricate sources.** If you can't find a source, say so.
2. **Never smooth over contradictions.** Surface them visibly.
3. **Confidence transparency**: Use qualifiers like "evidence strongly suggests", "limited data indicates", or "it is unclear" — never present uncertain findings as settled facts.
4. **No circular sourcing**: Don't cite Source A citing Source B as if it's independent evidence from two sources.
