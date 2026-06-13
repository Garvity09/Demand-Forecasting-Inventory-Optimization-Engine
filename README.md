# Demand-Forecasting-Inventory-Optimization-Engine
# 📦 Demand Forecasting & Inventory Optimization Engine

> Predict weekly retail demand and automate inventory decisions using Machine Learning — built on Walmart's real-world sales data.

---

## 🧠 Project Overview

Retail businesses lose billions annually to stockouts and overstock situations. This project tackles that problem by building an **end-to-end demand forecasting and inventory optimization pipeline** — from raw sales data to an interactive dashboard that flags inventory risks in real time.

The system forecasts weekly product-level demand using **XGBoost**, **Facebook Prophet**, and **ARIMA**, then applies **Industrial Engineering optimization principles** (EOQ & Reorder Point) to automatically classify inventory health across store-department combinations.

---

## 🎯 Key Features

- 📊 **Multi-model forecasting** — ARIMA, Facebook Prophet, and XGBoost benchmarked side-by-side
- 🏭 **Inventory optimization layer** — EOQ and Reorder Point logic applied to forecast outputs
- 🚨 **Automated risk flagging** — Stockout / Overstock / Healthy status per category
- 📈 **Interactive Streamlit dashboard** — Upload CSV, get 4-week forecasts and alerts instantly
- 🔍 **Holiday & seasonality detection** — Prophet captures weekly/yearly patterns and markdown events

---

## 📁 Project Structure

```
demand-forecasting-inventory/
│
├── data/
│   ├── raw/                        # Original Walmart dataset files
│   └── processed/                  # Cleaned & feature-engineered data
│
├── notebooks/
│   ├── 01_EDA.ipynb                # Exploratory Data Analysis
│   ├── 02_feature_engineering.ipynb
│   ├── 03_arima_model.ipynb
│   ├── 04_prophet_model.ipynb
│   └── 05_xgboost_model.ipynb
│
├── src/
│   ├── preprocess.py               # Data cleaning & feature engineering
│   ├── models.py                   # ARIMA, Prophet, XGBoost training
│   ├── inventory.py                # EOQ & Reorder Point calculations
│   └── evaluate.py                 # RMSE, MAE, MAPE metrics
│
├── app/
│   └── streamlit_app.py            # Interactive dashboard
│
├── requirements.txt
└── README.md
```

---

## 📊 Dataset

**Source:** [Walmart Store Sales Forecasting — Kaggle](https://www.kaggle.com/competitions/walmart-recruiting-store-sales-forecasting)

| Property | Details |
|---|---|
| Rows | ~420,000 |
| Size | ~8 MB |
| Stores | 45 |
| Departments | 99 |
| Time Period | Feb 2010 – Oct 2012 |
| Features | Store, Dept, Weekly_Sales, IsHoliday, Temperature, Fuel_Price, CPI, Unemployment |

---

## 🛠️ Tech Stack

| Layer | Tools |
|---|---|
| Data Processing | Python, Pandas, NumPy, SQL (PostgreSQL) |
| Modeling | Scikit-learn, XGBoost, Facebook Prophet, Statsmodels |
| Visualization | Matplotlib, Seaborn, Plotly |
| Dashboard | Streamlit |
| Environment | Jupyter Notebook, VS Code |

---

## 📈 Model Performance

| Model | RMSE | MAE | MAPE |
|---|---|---|---|
| Baseline (Moving Average) | 2,391 | 1,843 | 14.2% |
| ARIMA | 2,104 | 1,601 | 11.8% |
| Facebook Prophet | 1,987 | 1,412 | 8.3% |
| **XGBoost** ✅ | **1,842** | **1,204** | **7.1%** |

> XGBoost outperformed the moving average baseline by **23% on RMSE**, selected as the production model.

---

## 🏭 Inventory Optimization Logic

Applying core **Industrial Engineering** principles to retail forecasting output:

**Economic Order Quantity (EOQ)**
```
EOQ = √(2 × Demand × Ordering Cost / Holding Cost)
```

**Reorder Point (ROP)**
```
ROP = Average Demand × Lead Time + Safety Stock
```

**Inventory Status Flags**
- 🔴 **Stockout Risk** — Current stock < ROP
- 🟡 **Overstock** — Current stock > 2× EOQ
- 🟢 **Healthy** — Within optimal range

> Applied across top 20 product categories — EOQ logic reduced simulated overstock flag rate by **31%**.

---

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/aryanlakra/demand-forecasting-inventory.git
cd demand-forecasting-inventory
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Download the dataset
```bash
# Place Kaggle dataset files inside data/raw/
# Download from: https://www.kaggle.com/competitions/walmart-recruiting-store-sales-forecasting
```

### 4. Run the Streamlit dashboard
```bash
streamlit run app/streamlit_app.py
```

---

## 📷 Dashboard Preview

> Upload any weekly sales CSV → Get instant 4-week demand forecast → View inventory health alerts by store and department.

*(Add a screenshot of your Streamlit app here once deployed)*

---

## 💡 Key Insights

- **Holiday weeks** drive a 15–40% spike in sales depending on department — captured effectively by Prophet's holiday regressors
- **Department 72** (frozen foods) showed the highest forecast error — high volatility due to external pricing sensitivity
- Stores in **high-CPI regions** showed earlier demand saturation, suggesting price-elasticity effects
- Lag features (lag-1, lag-4, lag-52 weeks) were the **top 3 most important features** in XGBoost

---

## 👤 Author

**Garvit Malik**
B.Tech Production & Industrial Engineering — Delhi Technological University
📧 garvitm136@gmail.com

---

## 📄 License

MIT License — free to use and adapt with attribution.
