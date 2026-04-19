# 🛡️ CertGuard — AI Document Forgery Detector

> **VortexX × ThinkRoot Hackathon | NIT Trichy 2026**

A multilingual, AI-powered document forgery detection web application that uses multi-pipeline forensic analysis to detect tampered certificates, fake ID cards, forged cheques, and manipulated government documents.

---

## 🔗 Live Demo

> 🌐 **[View on ThinkRoot →]https://certguard-dashboard-zi3y1.thinkroot.app/

---

## 🧠 What It Does

CertGuard analyzes uploaded documents through **5 independent forensic pipelines** powered by Claude AI:

| Pipeline | Description |
|---|---|
| **Error Level Analysis (ELA)** | Detects JPEG recompression anomalies indicating spliced regions |
| **Copy-Move Detection** | Finds duplicated/cloned areas within a document image |
| **Signature Verification** | Checks handwriting consistency and signature authenticity |
| **OCR Text Analysis** | Extracts text and checks for typographic/content inconsistencies |
| **Wavelet Decomposition** | Surfaces high-frequency tampering artifacts invisible to the eye |

The AI synthesizes all signals into a **3-tier verdict**:
- ✅ **AUTHENTIC** (0–10% forgery probability)
- ⚠️ **SUSPICIOUS** (10–55% forgery probability)
- 🚨 **FORGED** (55–100% forgery probability)

---

## 🌍 Multilingual Support

Full UI + AI report output available in **8 languages**:

| Code | Language |
|---|---|
| EN | English |
| TA | தமிழ் (Tamil) |
| HI | हिन्दी (Hindi) |
| TE | తెలుగు (Telugu) |
| FR | Français (French) |
| AR | العربية (Arabic) — with RTL layout |
| DE | Deutsch (German) |
| ZH | 中文 (Chinese) |

---

## 🏗️ Architecture

```
CertGuard/
├── index.html          ← Single-file full application
├── README.md           ← This file
├── docs/
│   ├── architecture.md ← Technical design doc
│   └── screenshots/    ← UI screenshots
└── src/
    └── (future modular refactor)
```

### Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML5, CSS3 (CSS Variables, Grid, Flexbox) |
| Fonts | Syne (headings), JetBrains Mono (code), Lato (body) |
| AI Engine | Claude Sonnet (claude-sonnet-4-20250514) via Anthropic API |
| ELA Visualization | HTML5 Canvas — real-time pixel manipulation |
| Hosting | ThinkRoot.dev |
| Repo | GitHub |

---

## 🚀 How to Run Locally

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/certguard.git
cd certguard

# Open in browser (no build step needed!)
open index.html
# OR
python3 -m http.server 8080
# Then visit http://localhost:8080
```

> **Note:** The AI analysis requires an Anthropic API key. For the hackathon demo, the ThinkRoot deployment handles this.

---

## 🎯 Use Cases

- **Universities & Schools** — Verify degree certificates and mark sheets
- **Banks & NBFCs** — Authenticate cheques and financial documents
- **Government Offices** — Validate ID cards, ration cards, passports
- **HR Departments** — Screen employment certificates and experience letters
- **Insurance Companies** — Detect forged medical bills and claim documents

---

## 📊 How Forgery Scoring Works

```
Forgery Score = weighted_average(ELA, CopyMove, Signature, OCR, Wavelet)

Score Range    Verdict
0  – 10%  →   ✅ AUTHENTIC
10 – 55%  →   ⚠️ SUSPICIOUS  
55 – 100% →   🚨 FORGED
```

---

## 🖼️ Features

- ✅ Drag & drop or click-to-upload document
- ✅ Real-time ELA heatmap visualization on canvas
- ✅ Per-pipeline confidence score meters
- ✅ Typewriter-effect AI forensic report
- ✅ 4 analysis modes: Full / ELA Only / Signature / OCR
- ✅ 8-language UI with Arabic RTL support
- ✅ Zero dependencies — single HTML file, no npm, no build
- ✅ Fully responsive — works on mobile too

---


---

## 📚 References

- [DocAuth — trinity652/DocAuth](https://github.com/trinity652/DocAuth) — Inspiration & pipeline architecture
- [Anthropic Claude API](https://docs.anthropic.com) — AI vision & language model
- [Error Level Analysis — Farid, H. (2009)](https://farid.berkeley.edu) — ELA foundations
- [PhotoHolmes](https://arxiv.org/abs/2412.14969) — Image forensics library
- [CEDAR Signature Dataset](https://cedar.buffalo.edu/NIJ/data/) — Signature verification research

---


