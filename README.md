# LeanRS Emerging Markets Credit Analyst Skill

An AI-powered skill that turns your agentic platform into an emerging markets / high yield corporate credit analyst. It automates rating-agency-style credit research and writing using [Emerging Markets Data by LeanRS](https://www.leanrs.com) MCP tools — a structured database of income statement, balance sheet, cash flow, revenue/operating, debt, and EBITDA-reconciliation data, plus company filings and recent rating agency reports, for 200+ emerging market USD corporate credits.

## What this skill does

Once installed, your agent platform (e.g. Claude) can produce, from just a company name:

**Credit notes**
- **Credit Strengths & Competitive Position** — moat, market share, pricing power, cash flow durability through cycles
- **Debt Structure, Liquidity & Refinancing** — creditor hierarchy, maturity walls, 24-month liquidity coverage, pension-adjusted leverage
- **Run-Rate Cash Flow & FCF Sustainability** — normalized FCF, capex intensity, debt service coverage, stress resilience
- **EBITDA Adjustments & Earnings Quality** — a creditor-adjusted EBITDA built from itemized add-back haircuts
- **Currency Mismatch & FX-Adjusted Leverage** — USD-linkage of revenue/costs/capex, natural and derivative hedges, leverage under devaluation scenarios
- **Financial Policy & Capital Allocation** — guidance credibility, 5-year cash usage record, creditor-friendly vs. equity-centric verdict

Every note is written in rating-agency register (assertive, evidence-led, balanced), with every figure hyperlinked inline to its source in the database, the filing (with page number), or the rating report — never grouped into an end-of-section "Sources" list. Every note closes by naming the 2-4 points most worth a deeper follow-up, rather than a generic sign-off.

## Repository structure

```
skills-em-credit-analyst/
├── .claude-plugin/
│   └── plugin.json                    # Plugin manifest
├── skills/
│   └── leanrs-emerging-markets-credit-analyst/
│       ├── SKILL.md                   # Router
│       ├── references/
│       │   ├── shared/                # Citation rules, quality standards, sourcing mechanics, closing prompt
│       │   └── credit-analysis/        # The 6 notes + routing index
│       └── assets/templates/           # Shared header/voice/footer skeleton
├── scripts/
│   ├── build-skill.sh                 # Packages skills/.../ into a .skill file
│   └── build-plugin.sh                # Packages .claude-plugin/ + skills/ into a plugin zip
└── README.md, CONTRIBUTING.md, LICENSE, .github/workflows/cicd.yaml
```

This repo can be installed two ways — pick whichever your platform supports:

## Installation — as a Plugin (recommended, gives it a namespaced identity)

### Option 1: Download from Releases

1. Go to the [Releases page](https://github.com/Lean-Research/skills-em-credit-analyst/releases)
2. Download the latest `leanrs-emerging-markets-credit-analyst-plugin_<version>.zip`
3. Install it through whatever plugin-install flow your Claude surface offers (e.g. Claude Code's `/plugin marketplace add` + `/plugin install`, or an "upload as plugin" option if your interface has one)

### Option 2: Build from source

1. **Fork this repository**, then clone your fork locally
2. Customize the reference files under `skills/leanrs-emerging-markets-credit-analyst/`
3. Build the plugin package:
   ```bash
   ./scripts/build-plugin.sh 1.0.0
   ```
4. Find it at `scripts/output/leanrs-emerging-markets-credit-analyst-plugin_1.0.0.zip` and install it the same way as Option 1

## Installation — as a Skill only (no plugin manifest needed)

If your platform doesn't support Plugins, or you just want the credit-analysis behavior without the namespaced identity:

1. Download `leanrs-emerging-markets-credit-analyst_<version>.skill` from [Releases](https://github.com/Lean-Research/skills-em-credit-analyst/releases) — or build it yourself with `./scripts/build-skill.sh <version>`
2. Open [Claude](https://claude.ai) and navigate to **Customize → Skills**
3. Click **"+"** then **"+ Create skill"**, and upload the `.skill` file
4. The skill is off by default — toggle it on in your Skills list

## Customization ideas

When forking this repository, you might want to customize:

- **Note templates** — adjust the shared header/footer/voice in `skills/leanrs-emerging-markets-credit-analyst/assets/templates/rating-agency-note-template.md` to match your desk's house style
- **Sourcing priority** — each note's own file states how it weighs rating agency reports vs. the database vs. filings; adjust per your own methodology
- **Additional notes** — add a new file under `skills/leanrs-emerging-markets-credit-analyst/references/credit-analysis/` and register it in the routing table in `SKILL.md` and `references/credit-analysis/main.md`
- **Quality standards** — tighten or loosen the shared standards in `skills/leanrs-emerging-markets-credit-analyst/references/shared/output-quality-standards.md`
- **Plugin metadata** — update `.claude-plugin/plugin.json` (version, description, keywords) to match your fork

## Requirements

This skill requires the [Emerging Markets Data by LeanRS MCP](https://www.leanrs.com) connection to be configured in your agentic platform, for access to the structured financial database, company filings, and rating agency reports it's built on. Without that connection, the skill will tell you it can't proceed rather than guess at figures from general web knowledge.

## License

See [LICENSE](LICENSE) for details. © Lean Research Private Limited. Contact: info@leanrs.com
