# Tracking Spreadsheet

The tracking spreadsheet is the single source of truth for every application. It is updated from the moment an application is registered (workflow step 4).

**Who calculates what:**

- **The spreadsheet calculates per application:** the commission rate and amount, the consultants' share and its split between consultants, the amount the firm retains, and the expected payment month. These values are stored in each row.
- **The dashboard aggregates the current selection:** it reads those per-application values and adds them up for the filters chosen (month, consultant, status, search): totals received and pending, totals by party, totals by month, and the amount not yet scheduled. The dashboard does not recalculate commissions.

Demo file: [download mortgage-operations-demo.xlsx](https://raw.githubusercontent.com/CamilaNacli/mortgage-financing-operations/main/spreadsheet/mortgage-operations-demo.xlsx). It opens in Google Sheets or Excel, and every value in it is fictional.

## Tabs

| Tab | Purpose |
| --- | --- |
| **Read Me** | How the workbook is organized, business rules, assumptions and color legend |
| **Applications** | One row per application: inputs plus automatic calculations |
| **Commission Table** | Commission tiers, caps, fixed fee and split settings used by the formulas (yellow cells are inputs) |
| **Monthly Summary** | Totals received and pending, current-month production, application counts and a 12-month forecast of pending payments |

## Applications tab: fields

**Inputs** (filled in manually; most use drop-down lists):

| Field | Notes |
| --- | --- |
| Application ID | e.g., `APP-001` |
| Client | e.g., `Client 001` (fictional) |
| Registration Date | Date the application was registered |
| Property Value / Loan Amount | USD in the demo |
| Transaction Type | Drop-down: Standard Mortgage, Affordable Housing Program, Home Equity Loan |
| Financing Program | Drop-down: Program A, Program B, Program C, N/A |
| Home Equity Rate (monthly) | Only for home equity loans |
| Application Status | Drop-down with the 11 stages of the process (see [workflow](workflow.md#application-statuses)) |
| Assigned To | Drop-down: Consultant A, or Consultant A & Consultant B |
| Documents Submitted Date / Completion Date | Key milestones |
| Payment Status | Drop-down: Paid, Pending |
| Notes | Current pending item or next step |
| Expected Completion Month | Optional input (`yyyy-mm`), used before the completion date is known |

**Calculated automatically:**

| Field | Logic |
| --- | --- |
| Tier Reference Month | Month of the Completion Date, otherwise the Expected Completion Month, otherwise the month after registration |
| Monthly Production (Standard Mortgage) | Sum of standard mortgage loan amounts with the same reference month |
| Commission Rate | Tier based on monthly production (standard mortgage) or on the monthly interest rate (home equity) |
| Commission Amount (Firm) | Rate × loan amount, limited by the cap, or the fixed fee for the affordable housing program |
| Consultant Share % / Amount | Share of the firm commission paid to the consultant(s) |
| Consultant A / Consultant B Receives | Full share, or split equally when two consultants are assigned |
| Firm Retains | Commission minus the consultants' share |
| Expected Payment Month | Month after the completion date; empty while the application is in progress (shown as *Not scheduled* on the dashboard) |

## Why the monthly tier matters

For standard mortgages the rate does not depend on a single application. It depends on the **total production of the month**. When a new application pushes the month into a higher tier, every application in that month is recalculated at the new rate. The spreadsheet handles this automatically, so the expected values are always up to date.

In the demo data, November 2026 crosses the first threshold, so all standard mortgages in that month move from 0.50% to 0.65%.

> The tiers, rates, caps and split percentages in the demo are **illustrative**. They keep the logic of the real system but do not reproduce any real contract.
