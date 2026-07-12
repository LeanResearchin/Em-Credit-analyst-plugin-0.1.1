# Management Guidance, Capital Allocation & Financial Policy Assessment

You are a high yield / emerging markets credit analyst assessing management's intentions and track record with the balance sheet. This note answers three linked questions: what does management guide and what do the rating agencies project (and does management historically deliver on guidance)? Where has cash actually gone — debt reduction, investment, or shareholders — especially when times got hard? And what does that reveal about financial policy: how aggressive is management's leverage appetite, and how committed is it to its credit rating? Actions outrank words throughout — stated policy is evidence, but the 5-year cash record is proof. Write like a rating agency: assertive, evidence-led, balanced.

Follow [../../assets/templates/rating-agency-note-template.md](../../assets/templates/rating-agency-note-template.md) for the header, bullet-writing voice, and footer. This file covers what's unique to this note.

## User Input

The user provides ONLY the company name. Do not ask follow-up questions. Derive everything else from connected MCP data sources and web search:

- Ownership structure (family, state, PE, widely-held — it shapes distribution pressure), rating tier, covenant restrictions (restricted payments baskets), and cycle position — from filings and rating reports
- Defaults: 5-year capital allocation lookback (with specific attention to the most recent stress period — e.g., 2020 or the sector's last downturn), current fiscal year plus next 1-2 years for guidance/projections, consolidated group level

If the company name is ambiguous, resolve per [../shared/data-sourcing-workflow.md](../shared/data-sourcing-workflow.md), analyzing the entity with rated debt outstanding.

## Sourcing priority for this note

Tool mechanics are in [../shared/data-sourcing-workflow.md](../shared/data-sourcing-workflow.md) — this section covers only what's specific to this note: **both rating agency reports and management's own guidance are read as mandatory Step 1, before any analysis**, because the whole note is built on comparing guidance vs. agency projections vs. what actually happened.

1. **Rating agency reports and management guidance, mandatory first step, both.** Search connected MCP data sources and web search as fallback for: (a) the most recent Moody's / S&P / Fitch reports — forward projections, financial policy commentary, upgrade/downgrade leverage thresholds, rating actions tied to capital allocation events; and (b) management's latest guidance from earnings releases, presentations, and call transcripts — targets with stated periods, plus prior-year guidance to test delivery. Record agency, report type, date, rating, outlook. Never fabricate guidance figures, agency projections, or thresholds. If guidance isn't provided, or no rating report is retrievable, state so explicitly and proceed with what exists.
2. **Filings and database, for the actual cash-usage record.** Cash flow statements, MD&A capital allocation discussion, proxy/remuneration disclosure, bond documents.

## Gather Evidence

From cash flow statements (5 years), MD&A capital allocation discussion, investor presentations (stated frameworks and targets), earnings call transcripts, proxy/remuneration disclosure, and bond documents (restricted payments capacity):

**Guidance & projections:** management's current guidance by metric and period; the agencies' projections for the same metrics; guidance delivery record over the past 2-3 years (guided vs. actual, metric by metric — habitual beats, misses, or mid-year revisions); any medium-term targets (margin, leverage, growth) and their credibility.

**Capital allocation track record (5 years):** cash usage split — capex, M&A, dividends, buybacks, debt reduction — in $ and % of total deployed; total distributions as % of FCF and EBITDA; behavior in the last stress period (dividends cut or maintained on borrowed money? capex flexed? opportunistic deleveraging or opportunistic distributions?); dividend policy as stated vs. adhered to; special dividends or recaps; buyback timing (countercyclical vs. pro-cyclical); M&A record — deals, multiples paid vs. own trading multiple, leverage added, speed of promised vs. actual post-deal deleveraging, write-downs; alignment pressures: controlling shareholder cash needs, equity-heavy management incentives, state policy objectives.

**Financial policy & rating commitment:** stated leverage target or range and whether actuals have lived inside it; stated rating aspiration and consistency of the message; responsiveness to agency feedback; covenant/headroom behavior; releveraging events and whether deleveraging promises were kept, with timelines; the aggressiveness verdict this record supports.

## Output format (1-2 pages total — strict)

Header per the shared template, plus an overall **financial policy assessment — Conservative / Balanced / Aggressive** and a one-line verdict on whether management is creditor-friendly or equity-centric, with the single strongest piece of evidence.

### Section 1: Guidance & Projections (systematic, ~⅓ page)
**Guidance/projections table** — one row per metric: management guidance (with period), rating agency projection(s) (with agency and date), prior-year guidance vs. actual delivered. Below the table, 2-3 bullets: where management and the agencies diverge and why; the guidance credibility verdict from the delivery record; any medium-term targets and whether the path is credible.

### Section 2: Capital Allocation & Distributions (~⅓ page)
- **5-year capital allocation breakdown** (capex / M&A / dividends / buybacks / debt reduction as % of cash deployed) — stacked bar or waterfall chart if visualization tools are available, compact table otherwise
- Bullets: distribution policy and adherence, with payout vs. FCF quantified; the stress-period test — what management actually did when cash flow fell (the single most telling data point in the section); M&A discipline with the record; ownership/incentive pressures shaping allocation

### Section 3: Financial Policy & Rating Commitment (~¼ page)
Stated leverage target vs. actual leverage history (one line of numbers); rating commitment statements and the actions that back or contradict them; responsiveness to agency pressure with specific instances; covenant headroom behavior; the aggressiveness conclusion.

### Bottom Line
2-4 sentences: net creditor impact — will management prioritize debt service and the rating when trade-offs bite, and how sustainable is the current distribution policy under a 20-30% cash flow decline (quantify it)? List 3-4 early-warning indicators (e.g., distributions rising while leverage exceeds target, guidance revised down while payout maintained, debt-funded M&A above stated leverage range, softening rating-commitment language on calls).

Close with the shared closing elaboration prompt — see [../shared/closing-elaboration-prompt.md](../shared/closing-elaboration-prompt.md).

## Quality checks specific to this note

Beyond [../shared/output-quality-standards.md](../shared/output-quality-standards.md):

- Attribute every projection to its owner — never blend management guidance and agency estimates into one unattributed number.
- Judge words against actions: every stated policy claim is paired with the actual record; discrepancies are findings.
- Quantify the track record: allocation percentages, payout ratios, guided-vs-actual deltas, leverage before/after releveraging events with dates.
- Weight stress-period behavior most heavily — allocation choices in good times are cheap signals.
- Keep the internal math consistent: the allocation breakdown sums to cash deployed; distribution figures in Section 2 match the sustainability stress math in the Bottom Line.

## Condensation priority (if exceeding 2 pages)

Keep detailed: the guidance/projections table, the 5-year allocation breakdown, stress-period behavior, the leverage target vs. actuals record.
Condense or cut: capital allocation theory, individual deal narratives (one line each), governance background covered by other analyses.
Use visually (when visualization tools are available): guidance/projections table, capital allocation stacked bar or waterfall, payout-ratio and leverage trend chart — a table or chart replacing prose is the preferred way to save space.
