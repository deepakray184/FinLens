# FinLens

FinLens is a private, browser-based bank statement analyzer. Choose a statement to see spending categories, income, transaction details, yearly comparisons, UPI activity, and financial insights.

## Try it on GitHub Pages

FinLens is a static website: there is no server, build step, account, or API key to configure.

To publish it from this repository:

1. Open **Settings → Pages** on GitHub.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Select the `main` branch and the `/(root)` folder, then save.
4. Open the Pages URL shown in the Pages settings after deployment completes.

The app is served from [`index.html`](index.html) in the repository root.

## Use FinLens

1. Export your statement from your bank. CSV is recommended; Excel workbooks (`.xls`, `.xlsx`, `.xlsm`), text files (`.txt`, `.tsv`), and text-based PDFs are also supported.
2. Open FinLens and choose the statement file.
3. Review the overview and use the tabs to explore yearly trends, income, spending categories, transactions, UPI activity, and insights.

FinLens recognizes common column names, including:

- **Date:** `Date`, `Transaction Date`, or `Value Date`
- **Description:** `Description`, `Narration`, `Particulars`, or `Remarks`
- **Amounts:** separate `Debit` and `Credit` columns, or an `Amount` column with a transaction type such as `Type` or `Dr/Cr`
- **Optional:** `Balance`

CSV, TXT, and TSV files should include a header row and transaction dates in a recognizable format, such as `DD/MM/YYYY` or `YYYY-MM-DD`. Text files can use comma, semicolon, tab, or pipe separators. Excel files should contain a worksheet with the same transaction columns; FinLens looks through the workbook sheets for a recognizable table. If a file is not recognized, export it as CSV with the column headers included.

Text-based PDFs are supported experimentally. Scanned PDFs and image-only statements are not supported because FinLens does not include OCR. Password-protected PDFs can be unlocked in the browser.

## Privacy

Statement files are read and analyzed in your browser; FinLens does not send transaction data to a backend or store it on a server. The page loads its fonts, PDF.js, and SheetJS (used for reading Excel files) from public CDNs. For the best privacy, use a trusted device and a statement file exported directly from your bank.

## Development

Open `index.html` in a modern browser, or serve the repository root with any static web server. No package installation or build command is required.

## License

MIT
