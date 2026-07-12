# Citation & hyperlinking rules (non-negotiable)

Referenced by all six credit-analysis notes. These rules are identical regardless of which note you are producing.

Every figure, fact, or qualitative claim carries its source link inline, at the exact point it appears — in tables, bullet lists, charts, and formulas alike. Never group citations into a "Sources:" block at the end of a section or response.

## Hyperlink formats

Every figure extracted from the Emerging Markets Data by LeanRS MCP or a PDF must be hyperlinked when a `source_url` is present. Prefer the tool-returned `source_viewer_url` field when present; append `&pageoffset=N` when N > 0.

- **Figure from a PDF (page number mandatory):**
  `[USD 1,580M](https://mcp.leanrs.com/view-pdf?link={source_url}&pagenum={page_number}&pageoffset={N})`
  Optionally add `&search=term+here` to deep-link a phrase:
  `[MXN 108.4M](https://mcp.leanrs.com/view-pdf?link={source_url}&pagenum=23&pageoffset={N}&search=monitoring+costs)`
- **Figure from MCP structured data (no page number):**
  `[MXN 20,608M](source_viewer_url)`
  Never use this without-page-number format for a PDF-sourced figure.
- **Text claim from a filing:** "Monitoring costs rose 14x year-on-year ([Annual Report FY2023, p.23](url))"
- **Web-sourced claim:** full URL plus publication or retrieval date immediately after the claim — "Reference rate cut to 6.75% ([Banxico, March 2026](url))" — never only in a footer.

**Page numbers are mandatory for every figure or claim extracted from a PDF, without exception.** If you do not know the exact page number, go back and run `extract_pdf_text` on the specific page before presenting the data — never present a PDF-sourced figure or claim without its page number embedded in the link. A PDF citation without a page number is incomplete and must not appear in the response.

## Other rules

- **Derived/calculated metrics** (coverage ratios, conversion %, subordination %, leverage recalculations, and similar): the result itself has no hyperlink, but every input figure used in the calculation must be hyperlinked.
- **Missing data that cannot be resolved:** write "Not available in the database or filing for [period]."
- **Estimates:** always label as "⚠️ Estimate — [assumption/methodology]."
- **Web-sourced data:** cite the web source/link and keep it visually separate from filing/MCP data.
- End every response with: `[View Source Datasheet — Company Name](excel_url)` — one per company; omit silently if unavailable.
