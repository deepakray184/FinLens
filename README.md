# FinLens — Private Bank Statement Analyzer

FinLens turns a bank statement into a spending summary with category totals, monthly trends, yearly comparisons, and transaction details.

## Run on GitHub Pages

FinLens is a static site. It needs no Node.js server, package install, API key, or build step.

1. Push this repository to GitHub.
2. Open **Settings → Pages**.
3. Choose **Deploy from a branch**, select main and /(root), then save.
4. Open the Pages URL shown in Settings.

The site entry point is the root index.html.

## Use

Upload a CSV exported from your bank. FinLens recognizes common columns such as Date, Narration or Description, Debit, Credit, Amount, Type, and Balance. It reads and analyzes the file in your browser; transaction data is not uploaded.

PDF support is experimental and works only with text-based PDFs whose transaction rows can be recognized. Scanned PDFs need OCR and are not supported. Password-protected text PDFs can be unlocked in the browser. CSV is recommended.

Classification uses local transaction-description rules, so review categories and totals before relying on them. Different banks use different CSV formats; unsupported layouts show an error with the expected columns.

## Privacy

Statement contents remain on the device. FinLens does not send transactions to an API or store them in a server. The page loads its fonts and PDF.js library from public CDNs.

## License

MIT
