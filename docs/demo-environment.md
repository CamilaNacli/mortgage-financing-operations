# Demo Environment

> All data in this demo is fictional. See [Data confidentiality](data-confidentiality.md).

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

1. Use the filters (expected payment month, consultant, status, search) to explore the applications. Selecting a month turns the detail table into a month view.
2. Combine filters. All indicators, charts and tables follow the same selection.
3. Click **Clear filters** to return to the full view.

## Test it with your own copy of the spreadsheet

1. Download the [demo spreadsheet](https://raw.githubusercontent.com/CamilaNacli/mortgage-financing-operations/main/spreadsheet/mortgage-operations-demo.xlsx) and open it in Excel or Google Sheets.
2. Change an application, for example set its status to *Completed* and add a completion date, or mark a payment as *Paid*. The formulas recalculate the commission, split and expected payment month.
3. On the dashboard, click **◆ Load your own file** and select the edited `.xlsx`, or a `.csv` export of the Applications tab.

To connect the dashboard to your own published sheet, publish its Applications tab as CSV and open `https://camilanacli.github.io/mortgage-financing-operations/?csv=<published CSV link>`.

## Demonstration extensions

These items were added only to make the demo easier to explore. They are marked with ◆ on the dashboard and were not part of the original solution:

- application status filter and the "Applications by status" chart;
- loan volume indicator and the notes column in the detail table;
- **Load your own file** button.

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
