# ⚡ VoltShare

**ML-Based Peer-to-Peer Renewable Energy Pricing Platform**

VoltShare is a machine-learning-powered platform for exploring dynamic pricing in peer-to-peer (P2P) renewable energy trading.

The project combines an end-to-end ML pricing pipeline with an interactive web application. It uses electricity demand, solar generation, and weather data to estimate market conditions, generate pricing recommendations, and simulate P2P energy transactions.

🌐 **Live Demo:** https://aml-beta.vercel.app/

---

## 🚀 Overview

VoltShare connects machine learning with an interactive energy marketplace prototype.

The platform includes:

- **ML Pricing Pipeline** — Python-based preprocessing, feature engineering, model training, and evaluation
- **Dynamic Pricing Engine** — OLS and Random Forest estimation combined with grid-search pricing optimization
- **P2P Marketplace** — interactive workflow for listing, buying, and selling renewable energy
- **Pricing Recommendation UI** — model-driven pricing suggestions for energy sellers
- **Analytics Dashboard** — model performance, pricing logic, and market insights
- **Weather Integration** — historical weather alignment through Open-Meteo
- **Persistent Application State** — Zustand + localStorage, with optional Supabase integration
- **Production Deployment** — Vite/React application deployed through Vercel

---

## 🤖 Machine Learning & Pricing

The pricing pipeline evaluates multiple approaches to predicting electricity market conditions and generating P2P pricing recommendations.

### Models

The current implementation includes:

- **Ordinary Least Squares (OLS)** as a baseline model
- **Random Forest Regression** for nonlinear demand-price relationships
- **Weather feature ablation** to evaluate the incremental value of meteorological data
- **Grid-search pricing optimization** for generating recommended transaction prices

The full Python workflow is available at:

```text
notebooks/voltshare_pricing_ml.ipynb
```

### Model Performance

| Model | RMSE | MAE | R² |
|---|---:|---:|---:|
| OLS baseline | 0.3405 | 0.2211 | 0.8990 |
| Random Forest — no weather | 0.2892 | 0.1798 | 0.9272 |
| Random Forest — with weather | 0.2933 | 0.1822 | 0.9251 |

Random Forest improves predictive performance over the OLS baseline in the current dataset.

Weather variables did not improve out-of-sample accuracy with the current single-location weather proxy. This limitation is documented in the notebook and Analytics Dashboard and provides a direction for future model development.

---

## 📊 Data Sources

| Dataset | Source | Role |
|---|---|---|
| VIC1 electricity demand & price | AEMO 5-minute dispatch data | Demand and price modeling |
| Solar generation records | APVI / ARENA open data | Renewable supply proxy |
| Melbourne historical weather | Open-Meteo Archive API | Weather features and supply adjustment |

The repository includes the processed datasets required to reproduce the current ML workflow:

```text
src/data/price_and_demand_vic1.csv
src/data/Solar_Energy_Generation.csv
src/data/open_meteo_melbourne_hourly.csv
```

---

## 🛠 Tech Stack

### Machine Learning & Data

`Python` · `Pandas` · `NumPy` · `Scikit-learn` · `Statsmodels` · `Matplotlib` · `Jupyter`

### Frontend

`React` · `TypeScript` · `Vite` · `Tailwind CSS`

### Application State & Backend

`Zustand` · `localStorage` · `Supabase`

### Infrastructure

`Vercel` · `GitHub`

---

## 💻 Run Locally

Clone the repository:

```bash
git clone https://github.com/kz2595-coder/AML.git
cd AML
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Create a production build:

```bash
npm run build
```

Supabase is optional for the demo. Core application functionality can run with locally persisted state.

---

## 🧪 Run the ML Notebook

The complete Python ML pipeline is located at:

```text
notebooks/voltshare_pricing_ml.ipynb
```

The notebook covers:

1. Data loading and preprocessing
2. Feature engineering
3. OLS baseline estimation
4. Random Forest training
5. Model evaluation
6. Weather-feature ablation
7. Grid-search pricing optimization

Main Python dependencies:

```text
scikit-learn
pandas
numpy
statsmodels
matplotlib
```

---

## 📂 Project Structure

```text
src/
├── pages/
│   ├── AnalyticsDashboard.tsx   # Model explanation, charts, and evaluation
│   ├── SellEnergy.tsx           # ML pricing recommendation interface
│   ├── Marketplace.tsx          # P2P energy marketplace
│   ├── ActivityScreen.tsx       # Transaction and activity history
│   └── WalletScreen.tsx         # Balance and transaction management
│
├── services/
│   ├── aiService.ts             # OLS, Random Forest, and pricing optimization
│   └── weatherService.ts        # Open-Meteo weather integration
│
├── store/
│   └── index.ts                 # Zustand state with localStorage persistence
│
└── data/
    ├── vic1DemandBids.ts         # Preprocessed VIC1 demand data
    └── solarSupplyReports.ts    # Preprocessed solar supply data

notebooks/
└── voltshare_pricing_ml.ipynb   # End-to-end Python ML pipeline

supabase/                         # Optional backend configuration
```

---

## 👥 Collaboration & My Contributions

VoltShare was developed as a collaborative machine learning and product development project.

My work contributed across the **ML workflow, product implementation, and end-to-end deployment**, including:

- Developing and testing components of the ML-based pricing workflow
- Working with electricity-market and renewable-energy datasets
- Translating model outputs into an interactive pricing experience
- Supporting product and frontend implementation
- Integrating the ML workflow with the end-to-end product demo
- Deploying and maintaining the web application

This repository is maintained as my version of the collaborative project for continued development and experimentation.

---

## 🔭 Limitations & Future Development

The current version is a research and product prototype rather than a production electricity trading system.

Potential extensions include:

- Real-time AEMO market-data ingestion
- Multi-location weather and solar-generation features
- Time-series and more advanced pricing models
- API-based model serving
- Model explainability and uncertainty estimates
- More realistic P2P marketplace simulations
- Production-grade authentication and transaction infrastructure

---

## 📌 Project Status

VoltShare is currently maintained as an experimental ML + product prototype.

The live application demonstrates how a machine-learning workflow can be translated from model experimentation into an interactive user-facing product.
