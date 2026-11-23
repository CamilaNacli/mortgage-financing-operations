# Demo Environment

> All data in this demo is fictional (30 fictional applications, amounts in USD). See [Data confidentiality](data-confidentiality.md).

## Links

| | |
| --- | --- |
| Live dashboard | https://camilanacli.github.io/mortgage-financing-operations/ |
| Demo spreadsheet (download) | [mortgage-operations-demo.xlsx](https://raw.githubusercontent.com/CamilaNacli/mortgage-financing-operations/main/spreadsheet/mortgage-operations-demo.xlsx) |
| Data copy used as fallback | [data/applications.csv](../data/applications.csv) |

## How the demo is connected

The dashboard works the same way as the original solution:

1. A **demo Google Sheet** (fictional data only, separate from any real file) holds the applications.
2. Its **Applications** tab is published to the web as CSV.
3. The **dashboard** reads that CSV every time the page is opened or **Refresh** is clicked.

When the sheet changes, the dashboard shows the new data after Google updates the published copy, which usually takes a few minutes. If the published sheet cannot be reached, the dashboard uses the copy in `data/applications.csv`.

## Explore the dashboard

1. Use the filters (expected payment month, consultant, status, search). Selecting a month turns the detail list into a month view; **Not scheduled** lists the applications that do not have a payment month yet.
2. Combine filters. All indicators, charts and tables follow the same selection.
3. Click **Clear filters** to return to the full view.
4. On a phone, the application detail is a compact list (ID, status, payment). Tap a row, or focus it and press Enter or Space, to see the other fields.

## Test it with your own copy of the spreadsheet

1. Download the [demo spreadsheet](https://raw.githubusercontent.com/CamilaNacli/mortgage-financing-operations/main/spreadsheet/mortgage-operations-demo.xlsx) and open it in Excel or Google Sheets.
2. Change an application, for example set its status to *Completed* and add a completion date, or mark a payment as *Paid*. The formulas recalculate the commission, split and expected payment month.
3. On the dashboard, click **Load your own file ◆** and select the edited `.xlsx`, or a `.csv` export of the Applications tab.
4. While your file is shown, the data source line says so, and the main button changes to **Return to demo data**. Click it to discard your file and reload the published demo data.

The file must contain these columns: *Application ID, Client, Loan Amount, Application Status, Assigned To, Consultant Share Amount, Consultant A Receives, Consultant B Receives, Firm Retains, Expected Payment Month, Payment Status*. If any are missing, the dashboard lists them and keeps the current view.

To connect the dashboard to your own published sheet, publish its Applications tab as CSV and open `https://camilanacli.github.io/mortgage-financing-operations/?csv=<published CSV link>`.

> **Use fictional data only.** Any spreadsheet you publish as CSV for testing becomes publicly readable by anyone with the link. Never publish real client, financial or personal information.

## Demonstration extensions

These items were added only to make the demo easier to explore. They are marked with ◆ on the dashboard and were not part of the original solution:

- application status filter, the "Applications by status" chart and the count by status;
- "Total loan amount tracked" indicator and the notes field in the application detail;
- **Load your own file** and **Return to demo data**.

Everything else (indicators, commissions by party, monthly view, filters by month, consultant and search, detail tables, refresh from the spreadsheet, and the 11 application statuses) reproduces the original solution.

## Repository structure

```
mortgage-financing-operations/
├── index.html                       dashboard (GitHub Pages)
├── dashboard/dashboard-embed.html   same dashboard as a self-contained block
├── data/applications.csv            copy of the demo data (fallback)
├── spreadsheet/                     demo spreadsheet (.xlsx)
└── docs/                            documentation and screenshots
```
