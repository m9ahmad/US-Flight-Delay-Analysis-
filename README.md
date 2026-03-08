# Flight Delay & Cancellation Analysis (2024)

[![Data Size](https://img.shields.io/badge/Data%20Size-1M%2B%20Records-blueviolet)](https://www.kaggle.com/)
[![Analysis](https://img.shields.io/badge/Scope-Operational%20Resilience-blue)](https://github.com/)
[![ML](https://img.shields.io/badge/ML-XGBoost%20%26%20Regression-orange)](https://xgboost.ai/)

A deep-dive diagnostic of the US aviation system's operational health in 2024. This project quantifies the "Domino Effect" of flight delays, identifies structural bottlenecks in ground operations, and maps state-level fragility using a custom composite index.

## 📊 Executive Dashboard
* **On-Time Performance:** 89.60%
* **Systemic Completion Rate:** 97.78% (2.22% Cancellations)
* **Primary Bottleneck:** Late Aircraft Delay (Logistical Propagation)
* **Average Recovery Window:** ~2 Hours (Post-Weather Disruption)

---

## 🛠️ Tech Stack
* **Data Engineering:** Pandas (1.04M rows), NumPy
* **ML & Modeling:** XGBoost, Scikit-Learn (Linear Regression, Binary Classification)
* **Visualization:** Matplotlib, Seaborn, Plotly (Choropleth Mapping)

---

## 🔍 Key Analyses & Industrial Insights

### 1. Delay Anatomy: Weather vs. Logistics
Analyzed the tradeoff between intensity and volume.
* **The Findings:** While **Late Aircraft Delays** are more frequent, **Weather Delays** are more severe, averaging **~79 minutes** per affected flight. This suggests that airlines are better at managing scheduling hiccups than atmospheric disruptions.

### 2. The 'Chaos Hour' & Temporal Decay
Modeled the accumulation of system stress over a 24-hour cycle.
* **Result:** Identified **10 PM - 4 AM** as the peak 'Chaos Hour' (Avg 18.67m delay). This proves the "Domino Effect" peaks at night as minor morning delays compound into major late-night disruptions.

### 3. Operational Fragility Index (OFI)
Developed a custom **Composite Score (0-100)** for state-level resilience based on weather impact and cancellation volatility.
* **Highest Fragility:** Iowa (81.18) and North Dakota (76.38).
* **Application:** Highlights geographic regions where infrastructure is most susceptible to winter-driven systemic failure.

### 4. Ground Efficiency & 'Clogged' Cities
Calculated **Ground_Intensity** ($TaxiOut / Distance$) for short-haul routes.
* **Metric:** Identified cities like **Colorado Springs, CO** and **Lansing, MI** as operational bottlenecks where ground movements consume a disproportionate amount of total transit time.

### 5. Spillover Effect (Lagged Correlation)
Investigated how long it takes for an airport to recover after a disruption.
* **Discovery:** Found a positive correlation between hourly weather events and **taxi_out** times for the *subsequent 2 hours*. This quantifies the "recovery window" required for ground crews to normalize operations.

---

## 🤖 Machine Learning Outcomes

| Model | Task | Metric | Insight |
| :--- | :--- | :--- | :--- |
| **XGBoost** | Congestion Prediction | **AUC-PR: 0.19** | Severe congestion (>30m taxi) is highly stochastic; schedule features alone are insufficient for high-precision forecasting. |
| **Linear Regression** | Delay Propagation | **$R^2$: 0.01** | Late aircraft delays are driven by complex tail-rotation variables not captured in basic temporal features. |

---
