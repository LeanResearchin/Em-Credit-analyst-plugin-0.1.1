# Data sourcing mechanics (shared across all six notes)

This file covers the **mechanics** common to every note: how to call each Emerging Markets Data by LeanRS MCP tool, and how to handle the documents and gaps you find along the way. It does **not** cover sourcing *priority* — whether rating agency reports are read first, used only as a gap-filler, or treated as a primary source varies by note, because each note is testing a different thing. That priority is set in the note's own file, in its "Sourcing priority for this note" section, which points back here for the how.

## Resolving the company

If the company name is ambiguous (multiple issuers with similar names), call `search_company` to see the exact names on file, then resolve to the entity with rated debt outstanding — state explicitly which entity you analyzed.

## The seven tools, and when each is used

1. **`search_company`** — discover the exact company name on file, and confirm sector/currency/scale, before calling anything else.
2. **`get_sheet_catalog`** — inventory what structured data actually exists for the issuer (which sheets, which line items, which periods) before querying a specific sheet blind.
3. **`get_metrics`** — pull the actual numbers: specify `sheet_name` (IS, BS, CFS, Revenue, Debt, EBITDA, or sector variant), the `line_items`, and the `periods`. This is the primary source for figures once you know what's available.
4. **`compare_companies`** — pull one metric across multiple companies for the same periods, for peer/competitor benchmarking.
5. **`get_filing_links`** — locate the actual source documents (annual report, investor presentation, quarterly/interim report, offering memorandum) when the database doesn't hold the level of detail you need, or when you need to cite the original document.
6. **`extract_pdf_text`** — read a located filing. Pass the printed page label where you know it, not a guessed physical offset. If extraction fails or returns garbled text, retry with OCR or a different page/section before giving up.
7. **`get_sources`** — retrieve the source file reference and any Notes-sheet caveats for a company/sheet/period, whenever you need to cite the origin of a database figure.

## When a document can't be read

If `extract_pdf_text` still fails after retrying, search the web for the same document on a credible source (company IR site, securities regulator filing portal, stock exchange disclosure site) and read it there. Never substitute a plausible-sounding figure for one you couldn't actually retrieve.

## When a rating agency report is used, in any note

Record, and cite in the output: **agency, report type, date, rating, and outlook.** If no rating report is retrievable at all, state that explicitly at the top of the note and proceed on filings and database data alone — never fabricate an agency view, a rating, or a notching rationale.

## Web search

Across all six notes, open web search is supplementary, not primary — used for gaps the database/filings/rating reports leave (recent news, competitor moves, upcoming events, central bank/market data) or as a fallback when a specific document can't be located any other way. Keep web-sourced facts visually separate from filing/MCP data in the output, and cite them per [citation-hyperlinking-rules.md](./citation-hyperlinking-rules.md).
