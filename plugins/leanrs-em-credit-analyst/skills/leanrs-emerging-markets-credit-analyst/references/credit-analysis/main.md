# Credit analysis — index

Six rating-agency-style credit notes on an EM / high yield corporate issuer, run off the Emerging Markets Data by LeanRS MCP. The user provides only the company name; each note derives everything else.

## Tools (Emerging Markets Data by LeanRS MCP)

| Tool | Purpose |
|---|---|
| `search_company` | Resolve the exact company name, sector, currency, scale |
| `get_sheet_catalog` | Inventory what structured data exists for the issuer |
| `get_metrics` | Pull figures by sheet (IS, BS, CFS, Revenue, Debt, EBITDA), line items, periods |
| `compare_companies` | One metric across multiple companies, for peer benchmarking |
| `get_filing_links` | Locate source documents (annual report, presentation, etc.) |
| `extract_pdf_text` | Read a located filing, by printed page label |
| `get_sources` | Source file reference and caveats, for citation |

Full mechanics (retry/fallback behavior, ambiguous-company resolution, what to record for a rating report): [../shared/data-sourcing-workflow.md](../shared/data-sourcing-workflow.md).

## Routing

| User asks about | Note | Reference |
|---|---|---|
| Business quality, competitive moat, market share, "is this a good business" | Credit Strengths & Competitive Position | [credit-strengths-competitive-position.md](./credit-strengths-competitive-position.md) |
| Where bonds rank, maturities, refinancing risk, liquidity runway, pension deficit | Debt Structure, Liquidity & Refinancing | [debt-structure-liquidity-refinancing.md](./debt-structure-liquidity-refinancing.md) |
| Cash generation, FCF, capex intensity, whether cash covers debt service | Run-Rate Cash Flow & FCF Sustainability | [cash-flow-runrate-analysis.md](./cash-flow-runrate-analysis.md) |
| Adjusted EBITDA credibility, add-backs, earnings quality | EBITDA Adjustments & Earnings Quality | [ebitda-adjustments-earnings-quality.md](./ebitda-adjustments-earnings-quality.md) |
| FX exposure, hard-currency debt, devaluation sensitivity | Currency Mismatch & FX-Adjusted Leverage | [currency-mismatch-fx-leverage.md](./currency-mismatch-fx-leverage.md) |
| Management guidance, capital allocation, dividend policy, financial policy | Financial Policy & Capital Allocation | [financial-policy-capital-allocation.md](./financial-policy-capital-allocation.md) |

If a request spans more than one of these (e.g. "give me the full credit picture on X"), run each relevant note in sequence rather than blending them into one undifferentiated response — each has its own strict page budget and mandatory sections, and the person can ask for depth on any one afterward.

## Shared across all six

- Header, bullet-writing voice, and footer: [../../assets/templates/rating-agency-note-template.md](../../assets/templates/rating-agency-note-template.md)
- Citation and hyperlink formatting: [../shared/citation-hyperlinking-rules.md](../shared/citation-hyperlinking-rules.md)
- Quality standards common to all six: [../shared/output-quality-standards.md](../shared/output-quality-standards.md)
- Closing "go deeper on A/B/C" convention: [../shared/closing-elaboration-prompt.md](../shared/closing-elaboration-prompt.md)

Each note's own file covers what's genuinely specific to it — including, importantly, its own sourcing priority. **Sourcing priority is not shared**: some notes treat rating agency reports as a primary source, others treat them strictly as a gap-filler or sanity check only, and this is a deliberate difference tied to what each note is trying to establish, not an inconsistency to fix.
