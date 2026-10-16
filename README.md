# SDFX MRS Pipeline Dashboard

A single-file HTML dashboard for the MRS pendency report. It works on **SDFX locators only**.

## How to use

1. Open `index.html` in Chrome or Edge.
2. Click **Choose File(s)** or drop files. You can select several at once, for example the two split MRS pendency zips. Each can be a `.zip` or `.xlsx`. `.xls` and `.csv` also work for small files.
3. The files are read one after another. Only rows whose `Substore_Locator` contains `SDFX` are kept, so the dashboard, charts, filters and KPIs show SDFX data only.
4. Click **Run SDFX Pipeline**, then **Download Filtered Excel**.

## SDFX pipeline (unchanged)

| Step | Rule |
|---|---|
| 1 | Keep `SDFX` locators from `Substore_Locator` (done while loading) |
| 2 | Remove rows with a blank `DC_No` |
| 3 | Remove rows where `DC_Date` is today |

The Total Rows / After SDFX filter / After DC_No filter / Final rows counts are shown above the buttons. Total Rows is the number of rows scanned across all selected files.

## Notes

- Large files are read in a background worker, one file at a time, so the page stays responsive. Every sheet that has a `Substore_Locator` column is scanned.
- Rows from all selected files are combined. Duplicates across files are not removed.
- The charts and the Excel export need internet once to load Chart.js and the Excel library.
