# ⚡ VoltShare

**ML-Based Peer-to-Peer Renewable Energy Pricing Platform**

VoltShare is a collaborative machine learning and full-stack product project that explores dynamic pricing for peer-to-peer renewable energy trading.

The platform combines a machine-learning pricing pipeline with an interactive web application, allowing users to explore how energy prices can be estimated and optimized based on market and transaction conditions.

🌐 **Live Demo:** https://aml-beta.vercel.app/

---

## 🚀 What We Built

VoltShare combines machine learning, pricing optimization, and product development into an end-to-end prototype.

The project includes:

- **Machine Learning Pipeline** — Python-based data preprocessing, feature engineering, model training, and evaluation
- **Pricing Engine** — ML-assisted price estimation and grid-search optimization
- **Interactive Web App** — React + TypeScript interface for exploring pricing scenarios
- **Analytics Dashboard** — visualization of pricing and transaction insights
- **Backend Integration** — optional Supabase-based persistence and authentication
- **Production Deployment** — automated deployment through GitHub and Vercel

---

## 🤖 Machine Learning

The pricing pipeline explores multiple approaches to estimating renewable energy transaction prices, including:

- Ordinary Least Squares (OLS)
- Random Forest regression
- Feature engineering and model evaluation
- Grid-search-based pricing optimization

The ML workflow is documented in the `notebooks/` directory.

---

## 🛠 Tech Stack

**Machine Learning & Data**

`Python` · `Pandas` · `Scikit-learn` · `Jupyter`

**Frontend**

`React` · `TypeScript` · `Vite` · `Tailwind CSS`

**Backend & Infrastructure**

`Supabase` · `Vercel` · `GitHub Actions`

---

## 👥 Project Collaboration

VoltShare was developed as a collaborative project.

My contributions included work across the **machine-learning workflow, product development, and deployment**, including:

- Developing and testing parts of the ML-based pricing workflow
- Translating model outputs into an interactive product experience
- Supporting frontend/product implementation and iteration
- Integrating the technical workflow into an end-to-end demo
- Deploying and maintaining the web application

This repository is maintained as my version of the project for continued development and experimentation.

---

## 💻 Run Locally

Clone the repository:

```bash
git clone https://github.com/kz2595-coder/AML.git
cd AML
---

## Run the ML notebook

The full Python ML pipeline (OLS, Random Forest, weather ablation, grid-search pricing) is in:

```
notebooks/voltshare_pricing_ml.ipynb
```

Requirements: `scikit-learn`, `pandas`, `numpy`, `statsmodels`, `matplotlib` (auto-installed on first run).

Data files required (already in repo):
- `src/data/price_and_demand_vic1.csv` — VIC1 half-hourly demand & price
- `src/data/Solar_Energy_Generation.csv` — Melbourne solar generation
- `src/data/open_meteo_melbourne_hourly.csv` — historical weather cache

---

## Project structure

```
src/
  pages/
    AnalyticsDashboard.tsx   # Algorithm explanation + charts + model evaluation
    SellEnergy.tsx           # ML pricing recommendation UI
    Marketplace.tsx          # P2P listings (buy)
    ActivityScreen.tsx       # Unified history feed
    WalletScreen.tsx         # Balance + transactions
  services/
    aiService.ts             # Core pricing algorithm: OLS, Random Forest, grid search
    weatherService.ts        # Open-Meteo weather alignment
  store/
    index.ts                 # Zustand state (Zustand v6, localStorage-persisted)
  data/
    vic1DemandBids.ts        # Pre-processed VIC1 hourly demand bids
    solarSupplyReports.ts    # Pre-processed hourly solar supply reference
notebooks/
  voltshare_pricing_ml.ipynb # Full Python ML pipeline
```

---

## Data sources

| Dataset | Source | Use |
|---------|--------|-----|
| VIC1 electricity demand & price | AEMO 5-min dispatch data | Demand model training |
| Solar generation records | APVI / ARENA open data | Supply proxy |
| Melbourne historical weather | Open-Meteo archive API | Weather features + supply adjustment |

---

## Model performance (from notebook)

| Model | RMSE | MAE | R² |
|-------|------|-----|----|
| OLS baseline | 0.3405 | 0.2211 | 0.8990 |
| Random Forest (no weather) | 0.2892 | 0.1798 | 0.9272 |
| Random Forest (with weather) | 0.2933 | 0.1822 | 0.9251 |

Weather features did not significantly improve test-set accuracy with the current single-location proxy — this is discussed in the notebook and the Analytics Dashboard as a limitation and direction for future work.

---

## Tech stack

- **Frontend**: Vite + React + TypeScript + Tailwind CSS v3
- **State**: Zustand with localStorage persistence
- **Backend/Auth/DB**: Supabase (optional for demo)
- **Deployment**: Vercel
