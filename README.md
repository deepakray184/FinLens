# FinLens — AI Bank Statement Analyzer

> Decode your spending in seconds. Upload any Indian bank statement and get a full AI-powered financial breakdown — no API key needed by users.

![Status](https://img.shields.io/badge/Status-Active-brightgreen) ![License](https://img.shields.io/badge/License-MIT-blue) ![Powered by Claude](https://img.shields.io/badge/Powered%20by-Claude%20AI-blueviolet)

---

## Features

- 📊 **Overview** — Credits vs debits, savings rate, monthly trend
- 📅 **Yearly Trends** — Bar charts, savings line chart, year-wise table, category heatmap
- 💼 **Income** — Salary detection, all credit sources
- 🛍️ **Spending** — 15 expense categories with animated breakdown
- 💸 **Transactions** — Top debits and credits side by side
- 📲 **UPI Apps** — PhonePe, Google Pay, CRED, Paytm and more
- 💡 **Insights** — AI-generated financial insights with actual numbers
- 🔐 **Password-protected PDFs** — 3-step verify → unlock → analyze flow
- 🏦 **Supports** HDFC, ICICI, SBI, Axis, Kotak and all Indian banks (auto-detect)

---

## Project Structure

```
finlens-bank-analyzer/
├── server.js          ← Express proxy (keeps your API key secret)
├── package.json
├── .env.example       ← Copy to .env and add your key
├── .gitignore
├── render.yaml        ← One-click Render deploy
├── railway.json       ← One-click Railway deploy
├── vercel.json        ← One-click Vercel deploy
└── public/
    └── index.html     ← Full frontend (single file)
```

---

## Local Setup

### 1. Clone the repo
```bash
git clone https://github.com/YOUR_USERNAME/finlens-bank-analyzer.git
cd finlens-bank-analyzer
```

### 2. Install dependencies
```bash
npm install
```

### 3. Add your API key
```bash
cp .env.example .env
# Edit .env and paste your key from https://console.anthropic.com
```

### 4. Run
```bash
npm start
# → http://localhost:3000
```

For auto-reload during development:
```bash
npm run dev
```

---

## Deploy to the Web (Free)

### Option A — Render (recommended, free tier available)

1. Push this repo to GitHub
2. Go to [render.com](https://render.com) → **New Web Service**
3. Connect your GitHub repo
4. Render auto-detects `render.yaml` — just click **Deploy**
5. Go to **Environment** → add `ANTHROPIC_API_KEY` = your key
6. Done — your app is live at `https://finlens-xxxx.onrender.com`

### Option B — Railway

1. Go to [railway.app](https://railway.app) → **New Project → Deploy from GitHub**
2. Select this repo
3. Go to **Variables** → add `ANTHROPIC_API_KEY`
4. Railway auto-deploys — live in ~60 seconds

### Option C — Vercel

```bash
npm i -g vercel
vercel
# Follow prompts, then add env var:
vercel env add ANTHROPIC_API_KEY
vercel --prod
```

---

## Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `ANTHROPIC_API_KEY` | ✅ Yes | Your key from [console.anthropic.com](https://console.anthropic.com) |
| `PORT` | No | Server port (default: `3000`) |

> ⚠️ **Never commit your `.env` file.** It's in `.gitignore` by default.

---

## How It Works

```
Browser (user)
    │  uploads PDF/CSV
    │  PDF.js decrypts & extracts text locally
    │
    ▼
POST /api/analyze  →  server.js  →  Anthropic Claude API
                       (adds secret API key)
    │
    ▼
JSON response  →  Browser renders charts, tables, insights
```

Your API key lives only on the server — users never see it.

---

## Tech Stack

| | Technology |
|---|---|
| Frontend | Vanilla HTML/CSS/JS, PDF.js, inline SVG charts |
| Backend | Node.js + Express |
| AI | Anthropic Claude (`claude-sonnet-4-5`) |
| Deploy | Render / Railway / Vercel |

---

## License

MIT — free to use, modify, and deploy.
