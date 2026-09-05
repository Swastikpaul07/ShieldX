# ShieldX

**Intelligent Identity & Document Risk Screening**

ShieldX is a prototype web application for AI-assisted fake identity and document screening. It walks a case from document/voice upload through OCR extraction, tamper analysis, cross-document identity matching, voice authenticity analysis, authorized-source verification, and an explainable risk-fusion score — ending in a human reviewer decision that's written to a permanent audit trail.

This repository contains a **fully functional front-end prototype**. All "AI" analysis is produced by deterministic, seeded demo logic in the browser (the same inputs always produce the same outputs), standing in for the production inference services described in [Architecture](#architecture) below.

---

## Features

- **Authentication** — demo login/logout with four role-based accounts (RBAC)
- **Dashboard** — live stats, risk-distribution chart, screening-volume chart, source-verification chart, recent cases
- **New Screening wizard** — applicant details + document/selfie/voice upload → animated multi-stage analysis pipeline → results
- **OCR & document tamper analysis** — extracted fields with confidence scores, forensic tamper checks
- **Cross-document identity matching** — name/DOB/ID/address consistency + selfie liveness match
- **Voice authenticity analysis** — synthetic-speech detection with classification and flags
- **Authorized source / API verification** — simulated registry, KYC, watchlist and address-bureau checks
- **Risk Fusion Engine** — weighted, explainable composite score (0–100) → Genuine / Suspicious / High Risk verdict
- **Human reviewer validation** — approve / escalate / reject with mandatory notes, fully logged
- **Case management** — search, filter by risk/status/document type, responsive table
- **Case detail & reports** — tabbed case view, timeline audit trail, on-demand downloadable HTML report
- **Audit logs** — global, searchable, immutable action log
- **Settings** — RBAC permission matrix, encryption/session controls, privacy & data-retention controls, right-to-erasure anonymization

Fully responsive: desktop, tablet, and mobile (hamburger navigation, touch-friendly controls, no horizontal scrolling).

## Demo credentials

| Role | Username | Password |
|---|---|---|
| Administrator | `admin` | `admin123` |
| Analyst | `analyst` | `analyst123` |
| Reviewer | `reviewer` | `reviewer123` |
| Auditor | `auditor` | `auditor123` |

## Getting started

This is a single self-contained HTML file — no build step, no dependencies to install.

```bash
git clone <your-repo-url>
cd shieldx
```

Then either:

- **Open directly** — double-click `index.html`, or
- **Serve locally** (recommended, avoids browser file:// restrictions):
  ```bash
  python3 -m http.server 8000
  # then open http://localhost:8000
  ```

Chart.js and Google Fonts are loaded from public CDNs, so an internet connection is needed for full styling/charts; the app still runs without it.

## Architecture

The prototype is built as the front-end layer for the following reference stack:

| Layer | Technology |
|---|---|
| Frontend | React / HTML / CSS / JS, responsive UI |
| Backend API | Python + FastAPI |
| OCR engine | PaddleOCR / Tesseract |
| Image forensics | OpenCV (tamper & splice detection) |
| Data store | PostgreSQL |

In this repository, the backend, OCR, and computer-vision services are replaced with deterministic client-side simulations so the full workflow can be explored without any server infrastructure. Swapping in real services means replacing the functions in `index.html` under the `DETERMINISTIC "AI" SIMULATION ENGINE` section with calls to your FastAPI backend.

## Project structure

```
shieldx/
├── index.html    # entire application (markup, styles, logic)
├── README.md
└── LICENSE
```

## Disclaimer

This is a prototype for demonstration and evaluation purposes. Risk scores, OCR results, tamper flags, voice-authenticity classifications, and source-verification outcomes are simulated and must not be used for real identity or fraud decisions.

## License

MIT — see [LICENSE](LICENSE).
