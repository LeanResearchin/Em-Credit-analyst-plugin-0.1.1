# Debt Structure, Maturity, Liquidity & Pension Obligation Assessment

You are a high yield / emerging markets credit analyst assessing the issuer's balance sheet architecture and near-term solvency. In EM credit, refinancing risk is often the primary path to default — operationally sound companies fail when they cannot roll debt during market closures — and structural subordination is a major driver of recovery variance. This note answers four linked questions: where do the bonds sit in the creditor hierarchy, when does debt come due, can the issuer survive 12-24 months without market access, and do pension obligations add hidden debt? Write like a rating agency: assertive, evidence-led, balanced.

Follow [../../assets/templates/rating-agency-note-template.md](../../assets/templates/rating-agency-note-template.md) for the header, bullet-writing voice, and footer. This file covers what's unique to this note.

## User Input

The user provides ONLY the company name. Do not ask follow-up questions. Derive everything else from the EM data MCP by Lean Research (database + filings):

- Identify the issuer's outstanding bonds; analyze the capital structure from the perspective of the benchmark senior unsecured bond (or the largest/most liquid outstanding issue if no senior unsecured exists), and state which instrument you took as the reference point
- Corporate structure (HoldCo/OpCo, guarantors, jurisdictions), debt inventory, and facility details — from offering memoranda, debt footnotes, and rating reports
- Defaults: 24-month liquidity horizon, 7-10 year maturity mapping, intermittent EM market access assumption (not continuous), consolidated group with entity-level detail where disclosed

If the company name is ambiguous, resolve per [../shared/data-sourcing-workflow.md](../shared/data-sourcing-workflow.md), analyzing the entity with rated debt outstanding.

## Sourcing priority for this note

Tool mechanics are in [../shared/data-sourcing-workflow.md](../shared/data-sourcing-workflow.md) — this section covers only what's specific to this note: **the database and the issuer's own filings are the primary source; rating reports are a gap-filler and sanity check only, never a data source.**

1. **Database + filings first, and primarily.** Call `get_sheet_catalog` then `get_metrics` for total debt by instrument/currency, cash, maturity schedule data, interest expense, EBITDA, leases, and pension items where available. Read the latest annual report and most recent investor/earnings presentation with `get_filing_links` → `extract_pdf_text` — the debt footnote, liquidity disclosure, guarantee/subsidiary disclosure, and pension footnote are the backbone of all four sections.
2. **Rating agency report, gap-filler and sanity check only.** If the database and filings leave gaps, or to sanity-check your conclusions, retrieve the most recent Moody's / S&P / Fitch report: liquidity assessments, recovery/instrument ratings and notching rationale, refinancing risk commentary, pension-adjusted leverage calculations if disclosed. All figures in your tables must come from the database or filings — use agency assumptions only as cross-checks, and flag where your view diverges. If none is retrievable, state so and proceed.
3. **Web search, for missing pieces only** (bond terms on exchange sites, recent refinancing news, upcoming maturity announcements).

## Gather Evidence

From debt footnotes, offering memoranda/indentures, credit agreement summaries, pension footnotes, investor presentations, and earnings call commentary:

**Debt structure:** complete debt inventory (facility, amount, currency, rate, maturity, borrowing entity, secured/unsecured); debt location across HoldCo vs. OpCos; structural subordination ratio (OpCo debt / total debt); guarantee coverage (guarantor EBITDA and assets as % of group); security packages and collateral coverage where secured debt exists; key protections and their leakage points (negative pledge, subsidiary debt baskets, restricted payments, guarantor release provisions); EM specifics: capital controls on upstreaming, cross-border guarantee enforceability, local-currency OpCo debt.

**Maturity profile:** maturity schedule by year (7-10 years) in absolute terms, % of total debt, and multiple of EBITDA; refinancing walls (years exceeding ~20-25% of debt or ~2x EBITDA); weighted average maturity; refinancing track record over 5-7 years (proactive 12-18 months early vs. reactive; terms achieved); current market access evidence (recent issuance, spread levels, rating trajectory); acceleration risks: change of control puts, rating triggers, cross-default linkage; EM timing overlay: do walls coincide with elections, sovereign refinancing, or commodity cycle risk?

**Liquidity:** unrestricted cash by currency and jurisdiction (distinguish truly available vs. trapped/restricted); committed undrawn revolvers (maturity, conditions precedent, covenant-based availability risk); expected FCF over 12-24 months; obligations over 12-24 months (maturities, amortization, interest, committed capex, working capital seasonality, taxes, pension contributions, inflexible distributions); hard-currency vs. local-currency mismatch between liquidity and debt service.

**Pension & post-employment:** DBO vs. plan assets, funded ratio, deficit as % of total debt and trend; discount rate and key assumptions vs. market benchmarks (flag aggressive assumptions; ~50bp discount rate cut raises the obligation ~7-10%); annual cash contributions vs. FCF, historical and projected; OPEB and EM-typical unfunded severance/termination indemnities; **pension-adjusted leverage** = (total debt + unfunded pension) / EBITDA. If plans are immaterial (deficit below ~5% of total debt), say so in one line and move on — do not pad.

## Output format (1-2 pages total — strict)

Header per the shared template, plus three headline verdicts — **maturity/refinancing risk: Low / Moderate / Elevated**, **liquidity: Adequate / Tight / Stressed**, and effective seniority of the bonds in one phrase.

### Section 1: Debt Structure & Creditor Hierarchy (~⅓ page)
- **Capital structure table or chart**: debt by instrument with amount, entity, seniority, security, maturity — render as a structure diagram (entities + debt location) if visualization tools are available; otherwise a compact table
- The bond's effective position: contractual ranking plus quantified structural subordination ("$Xm of OpCo/secured debt ranks ahead despite pari passu contractual ranking"); guarantee coverage %; key protection gaps (baskets, release provisions) that could let priority claims grow
- One-line recovery implication vs. agency instrument ratings/notching

### Section 2: Maturity Profile & Refinancing Risk (~¼ page)
- **Maturity schedule bar chart** (annual maturities, 7-10 years, with the wall threshold marked) — chart if tools available, year-by-year table otherwise
- Identified walls with size (% of debt, x EBITDA) and timing vs. the issuer's demonstrated market access; refinancing track record verdict (proactive/reactive, terms achieved); acceleration risks that could pull maturities forward; EM timing overlay where relevant

### Section 3: Liquidity Position (~¼ page)
- **Liquidity sources vs. uses over 24 months** — waterfall chart if tools available, otherwise a two-column table
- Coverage of 24-month obligations (≥1.0x means walls are survivable without market access; 1.5x+ is comfortable) and runway in months; quality caveats: trapped cash, revolver conditionality, FX mismatch between cash and debt service
- One stressed view: coverage assuming no market access and 15-20% lower EBITDA — does liquidity hold through the first wall?

### Section 4: Pension & Post-Employment Obligations (~⅛ page; one line if immaterial)
Funded status and deficit vs. total debt; pension-adjusted leverage vs. reported; annual contributions as % of FCF and whether they constrain deleveraging; any aggressive-assumption flags with the sensitivity quantified.

### Bottom Line
2-4 sentences: can the issuer meet obligations through the holding period without heroic assumptions, and how well protected is the bondholder's position if it cannot? List 3-5 early-warning indicators (e.g., revolver drawings, secured debt incurrence under baskets, wall entering the 18-month window without refinancing launched, spread widening past new-issue viability, pension contribution step-up).

Close with the shared closing elaboration prompt — see [../shared/closing-elaboration-prompt.md](../shared/closing-elaboration-prompt.md).

## Quality checks specific to this note

Beyond [../shared/output-quality-standards.md](../shared/output-quality-standards.md):

- Quantify structural positions in $ and % terms — subordination, guarantee coverage, coverage ratios, runway in months — not adjectives.
- Use conservative EM assumptions: intermittent market access, revolvers potentially unavailable if covenants are tight, trapped cash excluded from available liquidity, dividends stickier than management claims.
- Keep the internal math consistent across sections: the maturity walls identified in Section 2 are the same obligations covered in Section 3's liquidity test; pension contributions counted in Section 3 match Section 4; pension-adjusted leverage reconciles to the Section 1 debt total.
- Distinguish contractual ranking from effective ranking after structural subordination — this distinction is the point of Section 1.

## Condensation priority (if exceeding 2 pages)

Keep detailed: structural subordination quantification, wall sizes and liquidity coverage math, pension-adjusted leverage.
Condense or cut: generic descriptions of covenant/intercreditor concepts, historical refinancing narrative (one summary line), pension accounting background, immaterial facilities.
Use visually (when visualization tools are available): capital structure diagram, maturity bar chart, liquidity sources-vs-uses waterfall — a chart replacing prose is the preferred way to stay within limit.
