# Rating-agency note skeleton

This is the shared shape for all six credit-analysis notes — the header, the writing voice, and the footer. It does **not** define which sections go in the body: those are specific to each note type and live in that note's own file under `references/credit-analysis/`. Use this file for the parts that are identical regardless of which of the six notes you're producing.

## Header (2-3 sentences, every note)

```
[Issuer name] ([Country] · [Sector]) — [Agency] [Rating]/[Outlook] ([Mon-YYYY])
[Reference instrument analyzed, if the note is instrument-specific]
Headline verdict: [the note's specific one-line takeaway — e.g. a Low/Moderate/Elevated rating,
a $ figure, or a one-line credit view — as defined in that note's own OUTPUT FORMAT section]
```

## Bullet-writing voice

Every substantive bullet is a short paragraph (2-4 sentences): lead with the credit point as an assertion, then immediately support it with data. Qualitative points are acceptable only with concrete supporting context (a named contract, a regulatory license held since a stated year, a track record through a named downturn) — never as bare adjectives.

Reference example (this is the register to match, not literal content to reuse):

> *"Leading domestic market position with pricing power: the company holds an approximately 45% share of the domestic cement market (vs. 18% for the #2 player), a position it has defended within ±2pp over 2020-2024, and passed through 2023-24 input cost inflation with price increases of 12% against COGS inflation of 9%, supporting EBITDA margins of 28-31% versus a peer average of ~22%."*

## Footer (every note, in this order)

1. **Bottom Line** — as defined in the note's own OUTPUT FORMAT section.
2. **Closing elaboration prompt** — see [closing-elaboration-prompt.md](../../references/shared/closing-elaboration-prompt.md).
3. **Source datasheet link** — `[View Source Datasheet — Company Name](excel_url)`, omitted silently if unavailable, per [citation-hyperlinking-rules.md](../../references/shared/citation-hyperlinking-rules.md).

## What's deliberately not here

Section names, what each section must cover, page-length targets, and condensation priorities — those differ by note and are the actual substance of each of the six files in `references/credit-analysis/`.
