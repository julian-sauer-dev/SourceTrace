# SourceTrace 🧾

**See where your money really goes.**

SourceTrace scans grocery receipts and reveals the corporate ownership behind every product you buy — showing which countries and companies ultimately profit from your purchases.

---

## 📱 Demo

### Landing Page
![SourceTrace Landing Page](assets/screenshots/Source-Trace-Landng.png)

### Receipt Analysis Result
![Receipt Analysis Result](assets/screenshots/Source-Trace-Result.png)

---

## 🎯 Problem

When you buy groceries, you see brand names — but who actually owns these brands? Which country are they incorporated in? Who are the ultimate beneficial owners?

**No consumer tool existed to answer these questions. Until now.**

---

## ✨ Features

- 📸 **Receipt Scanning** — Upload or photograph any grocery receipt
- 🏢 **Corporate Ownership** — Identifies parent companies for each product
- 🌍 **Jurisdiction Mapping** — Shows country of incorporation
- 📊 **Spend Breakdown** — Visual chart of where your money flows
- 🏦 **UBO Analysis** — Ultimate beneficial owners (institutional vs. family-owned)
- 🇩🇪 **German Market Focus** — Optimized for EDEKA, REWE, Lidl, Aldi receipts

---

## 📊 Example

### Input: Grocery Receipt
![Example Receipt](assets/screenshots/Example-Receipt.jpg)

### Output: Ownership Analysis
![Ownership Breakdown](assets/screenshots/Source-Trace-Result.png)

| Product | Brand | Parent Company | Jurisdiction |
|---------|-------|----------------|--------------|
| Nesquik | Nesquik | Nestlé S.A. | 🇨🇭 Switzerland |
| Nutella | Nutella | Ferrero Group | 🇱🇺 Luxembourg |
| G&G Mohren | Gut & Günstig | EDEKA Group | 🇩🇪 Germany |
| Ariel Pods | Ariel | Procter & Gamble | 🇺🇸 United States |

---

## 🏗️ Architecture

### System Overview
```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Lovable   │────▶│    n8n      │────▶│  Response   │
│  Frontend   │     │  Workflow   │     │   JSON      │
└─────────────┘     └──────┬──────┘     └─────────────┘
                           │
              ┌────────────┼────────────┐
              ▼            ▼            ▼
        ┌──────────┐ ┌──────────┐ ┌──────────┐
        │  Claude  │ │ SerpAPI  │ │Open Food │
        │  Vision  │ │ Lookup   │ │  Facts   │
        └──────────┘ └──────────┘ └──────────┘
```

### n8n Workflow
![n8n Workflow](assets/screenshots/n8n-workflow.png)

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|------------|
| Frontend | React (Lovable) |
| Workflow Automation | n8n |
| Receipt OCR | Claude 3.5 Sonnet Vision |
| Ownership Lookup | SerpAPI + Claude |
| Nutrition Data | Open Food Facts API |
| Hosting | Lovable Cloud + n8n Cloud |

---

## 🚀 Quick Start

### Prerequisites
- n8n Cloud account (or self-hosted)
- OpenRouter API key (for Claude)
- SerpAPI key (optional, for enhanced lookups)

### Setup

1. **Import n8n Workflow**
```bash
   # Import backend/n8n-workflow.json into your n8n instance
```

2. **Configure Credentials**
   - Add OpenRouter API key
   - Add SerpAPI key (optional)

3. **Deploy Frontend**
   - Fork the Lovable project or deploy from `/frontend`
   - Update API endpoint to your n8n webhook URL

4. **Test**
```bash
   curl -X POST https://your-n8n-url/webhook/analyze-receipt \
     -F "image=@receipt.jpg"
```

---

## 📈 Research Insights

This project was informed by deep research into German consumer behavior:

| Insight | Statistic | Source |
|---------|-----------|--------|
| Regional product preference | 77% | BMEL 2024 |
| Nutri-Score awareness | 88% | BMEL 2024 |
| Sustainable market share (DE) | 42% | NYU Stern |
| Sustainable market share (US) | 23.8% | NYU Stern |
| Label reading | 75% actively read labels | NSF Germany 2024 |

**Key finding:** No existing tool combined receipt scanning with corporate ownership data.

---

## 🗺️ Roadmap

- [x] Receipt OCR with Claude Vision
- [x] Corporate ownership identification
- [x] Jurisdiction breakdown visualization
- [ ] Open Food Facts integration (Nutri-Score)
- [ ] Ultimate Beneficial Owner (UBO) analysis
- [ ] Receipt history & trends
- [ ] Browser extension for online shopping
- [ ] Multi-language support

---

## 📁 Project Structure
```
sourcetrace/
├── README.md
├── LICENSE
├── assets/
│   └── screenshots/
│       ├── Example-Receipt.jpg
│       ├── n8n-workflow.png
│       ├── Source-Trace-Landng.png
│       └── Source-Trace-Result.png
├── frontend/
├── backend/
├── research/
└── docs/
```

---

## 📄 License

MIT License — see [LICENSE](LICENSE)

---

## 👤 Author

**Julian Sauer**

- LinkedIn: [your-linkedin]
- GitHub: [@JULIAN-SAUER-DEV](https://github.com/JULIAN-SAUER-DEV)

---

## 🙏 Acknowledgments

- [Open Food Facts](https://openfoodfacts.org) — Open product database
- [n8n](https://n8n.io) — Workflow automation
- [Lovable](https://lovable.dev) — Frontend development
- [Anthropic](https://anthropic.com) — Claude Vision API

---

<p align="center">
  <i>Built in 48 hours as a proof of concept for consumer transparency tools.</i>
</p>
