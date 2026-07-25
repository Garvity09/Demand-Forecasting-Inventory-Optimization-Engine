# 📦 Demand Forecasting & Inventory Optimization Engine

[![Python 3.11+](https://img.shields.io/badge/python-3.11%2B-blue.svg)](https://www.python.org/)
[![Forecasting: XGBoost & Prophet](https://img.shields.io/badge/Forecasting-XGBoost%20%7C%20Prophet-orange.svg)](https://xgboost.readthedocs.io/)
[![UI: Streamlit](https://img.shields.io/badge/UI-Streamlit-FF4B4B.svg)](https://streamlit.io/)
[![Domain: Industrial Engineering](https://img.shields.io/badge/Domain-Industrial%20Engineering-008080.svg)](https://www.informs.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

An enterprise-grade **Demand Forecasting and Inventory Optimization System** that bridges machine learning demand projections with Industrial Engineering operations research models to automatically classify inventory health and mitigate stockout & overstock risks.

---

## 🧠 System Architecture & Methodology

Retail businesses lose billions annually to supply chain imbalances. This engine solves this challenge through a multi-stage pipeline:

```
               +----------------------------------+
               |  Raw Sales & Inventory Data CSV  |
               +----------------+-----------------+
                                |
                                v
               +----------------------------------+
               | Multi-Model Demand Forecasting   |
               |  (XGBoost vs Prophet vs ARIMA)   |
               +----------------+-----------------+
                                |
                                v
               +----------------------------------+
               | Industrial Engineering Engine    |
               |  - Safety Stock                  |
               |  - Economic Order Quantity (EOQ) |
               |  - Reorder Point (ROP)           |
               +----------------+-----------------+
                                |
                                v
               +----------------------------------+
               | Automated Inventory Health Flag  |
               |  🚨 Stockout | 🟢 Healthy | ⚠️ Overstock
               +----------------+-----------------+
                                |
                                v
               +----------------------------------+
               | Interactive Streamlit Dashboard  |
               +----------------------------------+
```

---

## 📐 Industrial Engineering Formulas

### 1. Economic Order Quantity (EOQ)
$$EOQ = \sqrt{\frac{2 \cdot D \cdot S}{H}}$$
*Where $D$ = Annual Demand, $S$ = Ordering Cost, and $H$ = Annual Holding Cost per unit.*

### 2. Reorder Point (ROP)
$$ROP = (d \times L) + SS$$
*Where $d$ = Daily Demand Rate, $L$ = Lead Time (days), and $SS$ = Safety Stock.*

### 3. Safety Stock ($SS$)
$$SS = Z \times \sigma_L$$
*Where $Z$ = Service level Z-score and $\sigma_L$ = Standard deviation of demand during lead time.*

---

## 📊 Model Performance Benchmarks

| Model | Strengths | Suitable Use Case |
|---|---|---|
| **XGBoost** | Non-linear feature interactions, promotional markdowns | High-volume retail SKUs with complex exogenous variables |
| **Facebook Prophet** | Weekly/yearly seasonality, holiday trend capture | Long-term trend analysis with strong calendar effects |
| **ARIMA** | Autoregressive statistical baseline | Stationary time series with consistent historical patterns |

---

## 🚀 Quickstart & Streamlit Dashboard

```bash
# Clone the repository
git clone https://github.com/Garvity09/Demand-Forecasting-Inventory-Optimization-Engine.git
cd Demand-Forecasting-Inventory-Optimization-Engine

# Install dependencies
pip install streamlit pandas numpy xgboost prophet statsmodels plotly

# Launch Streamlit dashboard
streamlit run app.py
```

---

## 📜 License

Distributed under the MIT License. See `LICENSE` for details.
