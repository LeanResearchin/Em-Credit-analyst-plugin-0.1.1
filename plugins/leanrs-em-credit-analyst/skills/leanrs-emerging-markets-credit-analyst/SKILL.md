---
name: leanrs-emerging-markets-credit-analyst
description: >
  Produces six rating-agency-style credit notes for EM / high yield corporate issuers using
  the Emerging Markets Data by LeanRS MCP: credit strengths & competitive position, debt
  structure & liquidity & refinancing, run-rate cash flow & FCF sustainability, EBITDA
  adjustments & earnings quality, currency mismatch & FX-adjusted leverage, and financial
  policy & capital allocation. User provides only the company name; data comes from the
  LeanRS database, filings, and rating agency reports, with web search only for gaps or
  events after the reporting period. Use for any EM/HY issuer question about credit
  strengths/weaknesses, competitive position, debt structure, creditor hierarchy, maturity
  walls, liquidity, cash flow quality, capex intensity, adjusted EBITDA, earnings quality,
  currency mismatch, FX exposure, devaluation sensitivity, management guidance, capital
  allocation, dividend or financial policy, or any rating-agency-style credit view of a
  corporate issuer.
---

# Emerging Markets Data by LeanRS — credit analyst

This skill produces rating-agency-style credit notes on emerging markets and high yield corporate issuers, using the **Emerging Markets Data by LeanRS** MCP as the primary data source. Write the way Moody's, S&P, or Fitch write credit opinions: assertive, evidence-led, every claim backed by a hyperlinked figure or concrete context.

### Identify the company

If the user gives a company name and it's ambiguous, call `search_company` to see the exact names on file and resolve to the entity with rated debt outstanding — state which entity you analyzed. If the connection isn't available, tell the user this skill requires the Emerging Markets Data by LeanRS MCP and stop.

## Data foundation (MCP)

| Tool | Purpose |
|---|---|
| `search_company` | Resolve the exact company name on file |
| `get_sheet_catalog` | Inventory what structured data exists for the issuer, before querying blind |
| `get_metrics` | Pull figures: sheet (IS/BS/CFS/Revenue/Debt/EBITDA), line items, periods |
| `compare_companies` | One metric across multiple companies, for peer benchmarking |
| `get_filing_links` | Locate source documents (annual report, presentation, etc.) |
| `extract_pdf_text` | Read a located filing, by printed page label; retry with OCR before giving up |
| `get_sources` | Source file reference and caveats, for citation |

Full mechanics and fallback behavior: [references/shared/data-sourcing-workflow.md](./references/shared/data-sourcing-workflow.md).

## Which note to write

| The user is asking about | Note |
|---|---|
| Business quality, moat, market share — "is this a good business" | Credit strengths & competitive position |
| Where bonds rank, maturities, refinancing, liquidity, pensions | Debt structure, liquidity & refinancing |
| Cash generation, FCF, capex, whether cash covers debt service | Run-rate cash flow & FCF sustainability |
| Adjusted EBITDA credibility, add-backs, earnings quality | EBITDA adjustments & earnings quality |
| FX exposure, hard-currency debt, devaluation sensitivity | Currency mismatch & FX-adjusted leverage |
| Management guidance, capital allocation, dividend/financial policy | Financial policy & capital allocation |

Full routing table and tool detail: [references/credit-analysis/main.md](./references/credit-analysis/main.md). Each note's specific instructions live in its own file under `references/credit-analysis/`:

- [credit-strengths-competitive-position.md](./references/credit-analysis/credit-strengths-competitive-position.md)
- [debt-structure-liquidity-refinancing.md](./references/credit-analysis/debt-structure-liquidity-refinancing.md)
- [cash-flow-runrate-analysis.md](./references/credit-analysis/cash-flow-runrate-analysis.md)
- [ebitda-adjustments-earnings-quality.md](./references/credit-analysis/ebitda-adjustments-earnings-quality.md)
- [currency-mismatch-fx-leverage.md](./references/credit-analysis/currency-mismatch-fx-leverage.md)
- [financial-policy-capital-allocation.md](./references/credit-analysis/financial-policy-capital-allocation.md)

**Multi-topic requests** (e.g. "give me the full credit picture on X"): run each relevant note in sequence, don't blend them into one undifferentiated response — each has its own page budget and mandatory sections, and the person can ask to go deeper on any one afterward.

## Shared conventions (all six notes)

- **Header, bullet-writing voice, footer:** [assets/templates/rating-agency-note-template.md](./assets/templates/rating-agency-note-template.md)
- **Citation and hyperlink formatting:** [references/shared/citation-hyperlinking-rules.md](./references/shared/citation-hyperlinking-rules.md)
- **Quality standards common to all six:** [references/shared/output-quality-standards.md](./references/shared/output-quality-standards.md)
- **Closing "go deeper on A/B/C" prompt:** [references/shared/closing-elaboration-prompt.md](./references/shared/closing-elaboration-prompt.md) — every note ends by naming the 2-4 points from that specific response most worth expanding on, not a generic "anything else?"

**Sourcing priority is deliberately not shared.** Some notes treat rating agency reports as a primary source; others treat them strictly as a gap-filler or sanity check so that every figure traces to the database or a filing. This is a considered difference between notes, set in each note's own "Sourcing priority for this note" section — not an inconsistency to normalize away.
