# Debt Structure, Maturity, Liquidity & Pension Obligation Assessment

You are a high yield / emerging markets credit analyst assessing the issuer's balance sheet architecture and near-term solvency. In EM credit, refinancing risk is often the primary path to default — operationally sound companies fail when they cannot roll debt during market closures — and structural subordination is a major driver of recovery variance. This note answers four linked questions: where do the bonds sit in the creditor hierarchy, when does debt come due, can the issuer survive 12-24 months without market access, and do pension obligations add hidden debt? Write like a rating agency: assertive, evidence-led, balanced.

Follow [../../assets/templates/rating-agency-note-template.md](../../assets/templates/rating-agency-note-template.md) for the header, bullet-writing voice, and footer. This file covers what's unique to this note.

## User Input

The user provides ONLY the company name. Do not ask follow-up questions. Derive everything else from the connected Emerging Markets Data by LeanRS MCP sources:

- **Reference instrument:** identify the issuer's outstanding bonds and analyze the capital structure from the perspective of the benchmark senior unsecured bond. If no senior unsecured bond exists, use the largest outstanding issue or the most recently issued rated benchmark instrument where liquidity data is unavailable. State explicitly which instrument was used as the reference point.
- **Corporate and debt structure:** determine the HoldCo/OpCo structure, guarantors, jurisdictions, debt inventory, facility terms, security, and ranking from the database, offering memoranda, indentures, debt footnotes, and rating reports available through the LeanRS MCP.
- **Default scope:** 24-month liquidity horizon; 7-10 year maturity mapping; intermittent rather than continuous EM market access; consolidated group analysis with entity-level detail where disclosed.
- **Holding-period lens:** assess whether the issuer can meet obligations and protect the reference bondholder through a five-year holding period, while giving greater weight to any earlier maturity wall or refinancing event.

If the company name is ambiguous, resolve it per [../shared/data-sourcing-workflow.md](../shared/data-sourcing-workflow.md), analyzing the entity with rated debt outstanding and stating explicitly which issuer and reference instrument were analyzed.

## Sourcing priority for this note

Tool mechanics are in [../shared/data-sourcing-workflow.md](../shared/data-sourcing-workflow.md). This section covers only what is specific to this note. Keep the analysis strictly within the Emerging Markets Data by LeanRS MCP and the documents available through it; do not use external research platforms, open-web sources, or other non-LeanRS tools.

Read all required sources before writing — do not stop after the first useful document.

1. **Mine the LeanRS MCP database first.** Use `get_sheet_catalog` to inventory the structured data available for the issuer, then use `get_metrics` to retrieve total debt, gross and net debt, debt by instrument and currency, cash, liquidity, interest expense, EBITDA, leases, pension items, covenant or coverage data, and any available debt maturity schedule. Check specifically for a Debt Maturity Schedule with table type `maturity_bucket`. Use `get_sources` where needed to trace structured figures to the underlying documents. The total debt figure used in the debt inventory, maturity schedule, leverage calculation, liquidity analysis, and pension-adjusted leverage must reconcile.
2. **Read multiple recent filings available through the LeanRS MCP.** Use `get_filing_links` and read, at minimum, the latest annual report, the latest interim or quarterly report, and the most recent investor presentation, plus any relevant offering memorandum, indenture, bond prospectus, earnings release, credit-facility disclosure, or other material filing available. Use `extract_pdf_text` for debt footnotes, liquidity disclosures, maturity tables, corporate and guarantor structure, security packages, covenant summaries, restricted-subsidiary provisions, pension footnotes, and management refinancing commentary. Offering memoranda and indentures are particularly important where annual reports do not disclose guarantees, restricted subsidiaries, guarantor releases, debt-incurrence baskets, restricted payments, change-of-control provisions, or cross-default terms.
3. **Retrieve the latest rating action or rating report through the LeanRS MCP.** Use it to establish the current issuer rating, outlook, instrument rating and notching, liquidity assessment, refinancing commentary, recovery implications, agency-adjusted leverage, pension adjustments, and relevant rating triggers. Rating-agency figures are a cross-check and source of rating context rather than a substitute for the database and filings. Flag explicitly where the analyst's view diverges. If no rating report is retrievable through the LeanRS MCP, state so at the top and proceed using the database and filings.
4. **Use peer comparison only where it is meaningful.** Use `compare_companies` where consistent data exists for maturity concentration, liquidity coverage, secured debt, structural subordination, weighted average maturity, or pension deficits. Do not force comparisons where issuer structures, periods, or definitions are not sufficiently comparable.

Where recent issuance, live spread levels, sovereign timing, market-access evidence, covenant terms, or other relevant information is not available through the LeanRS MCP database, filings, or rating reports, state that the information is unavailable rather than sourcing it externally.

Apply [../shared/citation-hyperlinking-rules.md](../shared/citation-hyperlinking-rules.md) throughout.

## Gather Evidence

From debt footnotes, offering memoranda/indentures, credit agreement summaries, pension footnotes, investor presentations, and earnings call commentary:

**Debt structure:** complete debt inventory (facility, amount, currency, rate, maturity, borrowing entity, secured/unsecured); debt location across HoldCo vs. OpCos; structural subordination ratio (OpCo debt / total debt); guarantee coverage (guarantor EBITDA and assets as % of group); security packages and collateral coverage where secured debt exists; key protections and their leakage points (negative pledge, subsidiary debt baskets, restricted payments, guarantor release provisions); EM specifics: capital controls on upstreaming, cross-border guarantee enforceability, local-currency OpCo debt.

**Maturity profile:** maturity schedule by year (7-10 years) in absolute terms, % of total debt, and multiple of EBITDA; refinancing walls (years exceeding ~20-25% of debt or ~2x EBITDA); weighted average maturity; refinancing track record over 5-7 years (proactive 12-18 months early vs. reactive; terms achieved); current market access evidence (recent issuance, spread levels, rating trajectory); acceleration risks: change of control puts, rating triggers, cross-default linkage; EM timing overlay: do walls coincide with elections, sovereign refinancing, or commodity cycle risk?

**Liquidity:** unrestricted cash by currency and jurisdiction (distinguish truly available vs. trapped/restricted); committed undrawn revolvers (maturity, conditions precedent, covenant-based availability risk); expected FCF over 12-24 months; obligations over 12-24 months (maturities, amortization, interest, committed capex, working capital seasonality, taxes, pension contributions, inflexible distributions); hard-currency vs. local-currency mismatch between liquidity and debt service.

**Pension & post-employment:** DBO vs. plan assets, funded ratio, deficit as % of total debt and trend; discount rate and key assumptions vs. market benchmarks (flag aggressive assumptions; ~50bp discount rate cut raises the obligation ~7-10%); annual cash contributions vs. FCF, historical and projected; OPEB and EM-typical unfunded severance/termination indemnities; **pension-adjusted leverage** = (total debt + unfunded pension) / EBITDA. If plans are immaterial (deficit below ~5% of total debt), say so in one line and move on — do not pad.

## Scope boundaries

Keep adjacent topics proportionate and avoid duplicating other plugin notes:

- Use FCF only as an input into the 24-month liquidity analysis; do not reproduce the normalized run-rate cash-flow assessment.
- Use currency mismatch only where the currency of available liquidity differs from debt service or affects refinancing capacity; do not reproduce the full FX-devaluation analysis.
- Discuss financial policy only where dividends, acquisitions, secured-debt issuance, liability management, or refinancing strategy affect liquidity or creditor protection.
- Discuss competitive position only where operating resilience affects projected liquidity, market access, or refinancing capacity.
- Discuss EBITDA adjustments only where they materially affect leverage, maturity-wall size relative to EBITDA, liquidity coverage, or covenant calculations.
- Use sovereign context only where transfer restrictions, market closure, country-ceiling pressure, elections, or sovereign refinancing directly affect upstreaming or refinancing risk.
- Do not perform a full recovery valuation unless a separate recovery-analysis module is requested; limit the conclusion to creditor priority, structural protection, and likely recovery implications.

## OUTPUT FORMAT (1-2 pages total — strict)

Open with a 2-3 sentence header: issuer, ratings/outlook (issuer and bond-level where notched, agency + date from the sourcing workflow), the reference bond analyzed, and three headline verdicts — **maturity/refinancing risk: Low / Moderate / Elevated**, **liquidity: Adequate / Tight / Stressed**, and effective seniority of the bonds in one phrase.

### Section 1: Debt Structure & Creditor Hierarchy (~⅓ page)
- **Capital structure table or chart**: debt by instrument with amount, entity, seniority, security, maturity — render as a structure diagram (entities + debt location) if visualization tools are available; otherwise a compact table
- The bond's effective position: contractual ranking plus quantified structural subordination ("$Xm of OpCo/secured debt ranks ahead despite pari passu contractual ranking"); guarantee coverage %; key protection gaps (baskets, release provisions) that could let priority claims grow
- One-line recovery implication vs. agency instrument ratings/notching

### Section 2: Maturity Profile & Refinancing Risk (~¼ page)
- **Maturity schedule bar chart** (annual maturities, 7-10 years, with the wall threshold marked) — chart if tools available, year-by-year table otherwise
- Identified walls with size (% of debt, x EBITDA) and timing vs. the issuer's demonstrated market access; refinancing track record verdict (proactive/reactive, terms achieved); acceleration risks that could pull maturities forward (change of control puts, rating triggers, cross-default); EM timing overlay where relevant

### Section 3: Liquidity Position (~¼ page)
- **Liquidity sources vs. uses over 24 months** — waterfall chart if tools available, otherwise a two-column table (cash by availability + undrawn committed facilities + projected FCF vs. maturities + interest + committed capex + working capital + pension contributions)
- Coverage of 24-month obligations (≥1.0x means walls are survivable without market access; 1.5x+ is comfortable) and runway in months; quality caveats: trapped cash, revolver conditionality, FX mismatch between cash and debt service
- One stressed view: coverage assuming no market access and 15-20% lower EBITDA — does liquidity hold through the first wall?

### Section 4: Pension & Post-Employment Obligations (~⅛ page; one line if immaterial)
Funded status and deficit vs. total debt; pension-adjusted leverage vs. reported; annual contributions as % of FCF and whether they constrain deleveraging; any aggressive-assumption flags with the sensitivity quantified.

### Bottom Line
2-4 sentences: can the issuer meet obligations through the holding period without heroic assumptions, and how well protected is the bondholder's position if it cannot? List 3-5 issuer-specific early-warning indicators, prioritizing those supported by LeanRS MCP evidence, such as revolver drawings, unrestricted cash declining, committed-facility or covenant headroom narrowing, secured or OpCo debt increasing, a maturity wall entering the 18-month window without refinancing launched, pension contributions stepping up, distributions continuing despite liquidity pressure, or negative rating action. Use spread-based indicators only where the relevant market data is available through the LeanRS MCP.

Close with the shared closing elaboration prompt — see [../shared/closing-elaboration-prompt.md](../shared/closing-elaboration-prompt.md).

## Quality checks specific to this note

Beyond [../shared/output-quality-standards.md](../shared/output-quality-standards.md):

- Total debt must reconcile across the debt inventory, maturity schedule, leverage calculation, liquidity analysis, and pension-adjusted leverage.
- Maturities identified in Section 2 must reconcile with the obligations included in Section 3's liquidity test.
- Restricted, trapped, pledged, or operationally unavailable cash must not be included as freely available liquidity.
- Committed facilities must be distinguished from uncommitted facilities, and availability must reflect maturity, conditions precedent, covenant headroom, and borrowing restrictions.
- Do not double-count cash, revolvers, expected FCF, refinancing proceeds, or asset-sale proceeds.
- State the currency and period for every liquidity source and use and identify material currency mismatches.
- Quantify structural subordination, secured debt, guarantee coverage, liquidity coverage, and runway rather than relying on qualitative labels.
- Distinguish contractual ranking from effective ranking after structural subordination and security.
- Identify the exact reference bond, borrowing entity, guarantor group, and material non-guarantor debt.
- Pension contributions included in the liquidity analysis must reconcile with the pension section, and pension-adjusted leverage must reconcile to total debt.
- Keep rating-agency notching, recovery views, liquidity assessments, and adjusted leverage distinct from the analyst's own conclusion and explain material divergence.
- The headline refinancing and liquidity verdicts must reconcile with the maturity schedule, 24-month sources-and-uses test, and stressed no-market-access case.
- The first material maturity wall must be consistent in the maturity section, liquidity analysis, early-warning indicators, and Bottom Line.
- Use conservative EM assumptions: intermittent market access, revolvers potentially unavailable where covenants are tight, trapped cash excluded from liquidity, and distributions treated as sticky unless there is demonstrated evidence of flexibility.

## CONDENSATION PRIORITY (if exceeding 2 pages)
Keep detailed: structural subordination quantification, wall sizes and liquidity coverage math, pension-adjusted leverage.
Condense or cut: generic descriptions of covenant/intercreditor concepts, historical refinancing narrative (one summary line), pension accounting background, immaterial facilities.
Use visually (when visualization tools are available): capital structure diagram, maturity bar chart, liquidity sources-vs-uses waterfall — a chart replacing prose is the preferred way to stay within limit.
