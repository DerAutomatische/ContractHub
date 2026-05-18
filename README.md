# ContractHub

A lightweight contract management system built in Excel (.xlsm) for small teams and startups. Tracks supplier contracts, SaaS subscriptions, and client agreements with a live dashboard, 90-day expiry alerts, and a rolling cash flow forecast.

---

## What it does

- **Dashboard** — live KPIs: monthly spend, annual average, contracts expiring in 90 days
- **Suppliers sheet** — all vendor and SaaS contracts with status tracking
- **Clients sheet** — client contracts
- **Forecast sheet** — rolling monthly cash flow by contract, configurable horizon

---

## Getting started

1. Download `ContractHub_template.xlsm`
2. Open in **Excel Desktop** (not browser — VBA won't work online)
3. Click **Enable Macros** when prompted
4. Add your contracts in the Suppliers sheet
5. Click the **Refresh Dashboard** button

> Always save as `.xlsm` — saving as `.xlsx` removes the VBA macro.

> **Excel locale note:** The template was built on German Excel which uses `;` as the formula separator. If you're on English Excel and see formula errors after opening, simply re-enter the affected formulas using `,` instead of `;`. All formulas are documented in `skill/SKILL.md`.

---

## Adding a contract

Open the **Suppliers** sheet and add a new row at the bottom. Fill in:

| Column | Field | Format |
|--------|-------|--------|
| A | Counterparty | Text |
| B | Type | supplier / saas / lease / hr / other |
| C | Netto | Number only (no € sign) |
| D | Brutto | Number only (no € sign) |
| E | Frequency | Monthly / Quarterly / Semi-annual / Annual / One-time |
| F | StartDate | DD.MM.YYYY |
| G | EndDate | DD.MM.YYYY (leave blank if open-ended) |
| H | NoticeDays | Number of days (e.g. 90) |
| I | AutoRenewal | Yes or No |
| L | Status | Active / Review / Terminate / Expired |
| M | Notes | Free text |

**Important:** Columns J, K, N contain formulas — copy them from the row above, never type manually.

After adding a row: click **Refresh Dashboard** → Ctrl+S → confirm SharePoint check-in.

---

## Contract status

| Status | Meaning |
|--------|---------|
| Active | Running normally |
| Review | Needs attention |
| Terminate | Cancellation in progress |
| Expired | Ended — excluded from all calculations |

---

## Forecast

The Forecast sheet shows expected monthly costs per contract. Change the number in cell **B1** to set how many months to display (e.g. 6, 12, 18).

---

## Claude AI skill

The `skill/SKILL.md` file contains a Claude skill for ContractHub. Install it in a Claude Project to get an AI assistant that already knows the full architecture, every formula, and how to troubleshoot common errors.

**To set up the Claude Project:**
1. Go to [claude.ai](https://claude.ai) → Projects → New Project
2. Name it `ContractHub Assistant`
3. Paste the contents of `skill/SKILL.md` into the project instructions
4. Anyone on the team can then ask questions in English or German

---

## Requirements

- Microsoft Excel Desktop (Windows or Mac)
- Macros must be enabled on open
- Recommended: stored on SharePoint for team access

---

## Repo structure

```
ContractHub/
├── ContractHub_template.xlsm   ← template with dummy data
├── docs/
│   └── ContractHub_QuickStartGuide.docx      ← user guide
└── skill/
    └── SKILL.md                ← Claude AI skill
```

---

## License

MIT — free to use and adapt.
