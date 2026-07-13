# German Electricity Demand Forecasting
## 7PAM2016 — Time Series Modelling Case Study
**MSc Data Science | University of Hertfordshire**

**Student:** Gopikrishna Godishala | **ID:** 24090533 
---

## Overview

This project builds a complete time series forecasting pipeline for German weekly 
electricity demand (2015–2020) using data from Open Power System Data (OPSD). 
Six model classes are implemented and compared against a Seasonal Naive baseline 
over a 2-year (104-week) holdout period.

---

## Models Implemented

| Model | Type | RMSE (MW) | Skill vs Seasonal Naive |
|-------|------|-----------|------------------------|
| Stacked LSTM (168h) | Deep Learning | 120.7 | +0.96 |
| BiLSTM (168h) | Deep Learning | 1,178.2 | +0.62 |
| Random Forest | Feature-Based | 2,695.4 | +0.12 |
| Gradient Boosting | Feature-Based | 2,820.1 | +0.08 |
| Seasonal Naive | Benchmark | 3,073.5 | 0.00 |
| SARIMA(1,0,0)(1,0,0)[52] | Statistical | 3,247.2 | -0.06 |

---

## Data Sources

- **Electricity load:** [Open Power System Data](https://data.open-power-system-data.org/time_series/)  
  File: `time_series_60min_singleindex.csv`  
  Column: `DE_load_actual_entsoe_transparency`

- **Temperature:** [Open-Meteo Archive API](https://archive-api.open-meteo.com/v1/archive)  
  Location: Berlin (52.52°N, 13.41°E) — representative German temperature

---

## Project Structure
├── run_german_electricity_forecasting_gopikrishna_FINAL.ipynb   # Main notebook
├── README.md


### Notebook Sections

| Part | Description |
|------|-------------|
| Part 1 | Data download, resampling, EDA, STL decomposition, stationarity tests |
| Part 2 | Benchmark models — Mean, Naive, Seasonal Naive, Drift |
| Part 3 | SARIMA — stepwise AIC order selection, residual diagnostics, forecast |
| Part 4 | SARIMAX — HDD/CDD temperature covariates, conditional forecast |
| Part 5 | Random Forest and Gradient Boosting with lag/calendar features |
| Part 6 | Stacked LSTM and BiLSTM on hourly data (168h look-back) |
| Part 7 | Model comparison, metrics table, analysis questions |

---

## How to Run

### Google Colab (recommended)

1. Open `run_german_electricity_forecasting_gopikrishna_FINAL.ipynb` in Colab
2. Upload `time_series_60min_singleindex.csv` to the Colab file browser
3. Click **Runtime → Run all**

### Local

```bash
pip install pandas numpy matplotlib statsmodels pmdarima scikit-learn tensorflow requests
jupyter notebook run_german_electricity_forecasting_gopikrishna_FINAL.ipynb
```

---
---

## References

- Hyndman, R.J. and Athanasopoulos, G. (2021) *Forecasting: Principles and Practice*. OTexts.
- Hochreiter, S. and Schmidhuber, J. (1997) 'Long Short-Term Memory', *Neural Computation*, 9(8).
- Breiman, L. (2001) 'Random Forests', *Machine Learning*, 45(1).
