# FinLens — AI Bank Statement Analyzer

> Decode your spending in seconds. Upload any Indian bank statement and get a full financial breakdown powered by Claude AI.

![FinLens Preview](https://img.shields.io/badge/Status-Active-brightgreen) ![License](https://img.shields.io/badge/License-MIT-blue) ![Powered by Claude](https://img.shields.io/badge/Powered%20by-Claude%20AI-blueviolet)

---

## What It Does

FinLens is a single-file web app that lets you upload a bank statement (PDF or CSV) and instantly get:

- A full breakdown of credits, debits, salary, and savings rate
- Spending categories across Food, Shopping, Transport, EMI, Investments, and more
- UPI app analysis — PhonePe, Google Pay, CRED, Paytm and others
- Yearly trends with charts and tables — perfect for multi-year statements
- AI-generated insights about your financial patterns

Everything runs in the browser. Your file is never uploaded to any server — it's read locally and only the extracted text is sent to the Anthropic API for analysis.

---

## Features

### 📊 Overview Tab
- Debit vs Credit split bar with percentages
- Savings rate ring chart
- Opening / closing balance, avg monthly spend
- Monthly credit vs debit trend chart

### 📅 Yearly Trends
- Annual bar chart (credits vs debits per year)
- Savings rate line chart across years
- Year-wise summary table with net change, savings %, transaction count
- Category spend heatmap — see which categories grew year over year

### 💼 Income Tab
- Salary detection (amount, employer, credit dates)
- All income sources: salary, interest, refunds, P2P received, other credits

### 🛍️ Spending Tab
- 15 expense categories with animated bars and % of total debits
- Food & Dining, Groceries, Shopping, Transport, Bills, Health, Education, Rent, EMI, SIP, Subscriptions, ATM, and more

### 💸 Transactions Tab
- Top debits and top credits side by side
- Each entry shows date, category, and running balance

### 📲 UPI Apps Tab
- Detects PhonePe, Google Pay, CRED, Paytm, Amazon Pay, BHIM, and more
- Per-app sent/received amounts and transaction counts
- Top UPI payees and merchants
- UPI-specific insights

### 💡 Insights Tab
- 5–6 AI-generated insights with actual numbers
- Color-coded: ✅ Good · ⚠️ Warning · 🚨 Bad · 💡 Info

### 🔐 Password Protected PDFs
- Auto-detects encrypted PDFs
- 3-step flow: Enter password → Verify (confirms correct before analyzing) → Analyze
- Works with any password — DOB, mobile number, customer ID, account number, etc.

---

## Supported Banks

| Bank | PDF | CSV |
|------|-----|-----|
| HDFC Bank | ✅ | ✅ |
| ICICI Bank | ✅ | ✅ |
| SBI | ✅ | ✅ |
| Axis Bank | ✅ | ✅ |
| Kotak Mahindra | ✅ | ✅ |
| Other banks | ✅ Auto-detect | ✅ |

---

## Getting Started

### Prerequisites

- An [Anthropic API key](https://console.anthropic.com/) — the app calls `claude-sonnet-4-5` via the Anthropic Messages API
- A modern browser (Chrome, Firefox, Edge, Safari)
- No Node.js, no backend, no build step required

### Setup

1. Clone or download this repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/finlens-bank-analyzer.git
   cd finlens-bank-analyzer
   ```

2. Open `bank-analyzer.html` directly in your browser — or serve it locally:
   ```bash
   # Python
   python -m http.server 8080

   # Node
   npx serve .
   ```

3. The app calls the Anthropic API from the browser. Make sure your API key is configured in the Anthropic console with appropriate CORS permissions, or run it through a local proxy.

> **Note:** Calling the Anthropic API directly from a browser requires that your API key is allowed for browser/CORS usage. For production use, route API calls through a lightweight backend or serverless function to keep your key secure.

---

## How It Works

```
User uploads PDF/CSV
        │
        ▼
PDF.js extracts text locally in the browser
(password-protected PDFs are decrypted client-side)
        │
        ▼
Extracted text sent to Anthropic Claude API
(claude-sonnet-4-5, up to 16,000 output tokens)
        │
        ▼
Claude returns structured JSON with:
summary · salary · income_sources · expense_categories
top_transactions · monthly_data · yearly_data · upi_analysis · insights
        │
        ▼
JavaScript renders charts, tables, and insights in the browser
```

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| UI | Vanilla HTML, CSS, JavaScript (no framework) |
| PDF parsing | [PDF.js 3.11](https://mozilla.github.io/pdf.js/) |
| AI analysis | [Anthropic Claude API](https://docs.anthropic.com/) (`claude-sonnet-4-5`) |
| Fonts | DM Serif Display, DM Mono, Syne (Google Fonts) |
| Charts | Pure CSS + SVG (no chart library) |
| Hosting | Any static host — GitHub Pages, Netlify, Vercel |

---

## File Structure

```
finlens-bank-analyzer/
├── bank-analyzer.html   # The entire app — self-contained single file
└── README.md
```

---

## Privacy

- **Your file never leaves your device.** PDF.js reads and decrypts the file entirely in the browser.
- Only the extracted plain text is sent to the Anthropic API for analysis.
- No data is stored, logged, or shared beyond the API call.
- Anthropic's data handling is governed by their [privacy policy](https://www.anthropic.com/privacy).

---

## Deploying to GitHub Pages

1. Push the repository to GitHub
2. Go to **Settings → Pages**
3. Set source to `main` branch, root folder
4. Your app will be live at `https://YOUR_USERNAME.github.io/finlens-bank-analyzer/bank-analyzer.html`

---

## Known Limitations

- Very large statements (10+ years, thousands of transactions) may take 20–30 seconds to analyze due to API processing time
- The free Anthropic API tier has rate limits — if you hit a 429 error, wait a minute and retry
- CSV format support depends on the bank's export format; HDFC and ICICI CSVs are best supported
- UPI detection relies on narration keywords in the statement — banks with non-standard narrations may show lower accuracy

---

## Contributing

Pull requests are welcome. Some ideas for improvements:

- [ ] Multi-file upload (merge statements from different periods)
- [ ] Export analysis as PDF report
- [ ] Budget vs actual comparison
- [ ] Recurring payment detection
- [ ] Dark/light theme toggle
- [ ] Support for credit card statements

---

## License

MIT License — free to use, modify, and distribute.

---

## Acknowledgements

- Built with [Claude](https://www.anthropic.com/claude) by Anthropic
- PDF parsing via [PDF.js](https://mozilla.github.io/pdf.js/) by Mozilla
- Fonts by [Google Fonts](https://fonts.google.com/)
