# Time Series Revenue Forecasting with Regression Analysis

A Python-based project applying linear regression and time series techniques to forecast quarterly company revenue, using Apple Inc. as a case study.

## Overview

This project builds a series of increasingly sophisticated OLS (Ordinary Least Squares) regression models to forecast quarterly revenue, starting with a simple time-trend model and progressing to a model that accounts for seasonality through dummy variables and interaction terms. The workflow mirrors a real-world forecasting pipeline: visualize the data, engineer features, split into training/testing sets, fit and validate the model, then generate out-of-sample forecasts.

## What This Project Covers

- **Data preparation** — importing quarterly sales data, converting date fields for time series analysis, and constructing a sequential time-period variable
- **Exploratory visualization** — plotting historical revenue trends to identify patterns before modeling
- **Train/test splitting** — an in-time 75/25 split appropriate for time series data (as opposed to random splitting)
- **Baseline model** — a simple linear regression of revenue on time
- **Seasonality-adjusted model** — extending the model with a dummy variable to flag a specific fiscal quarter, plus an interaction term (time × dummy) to capture how the trend itself shifts during that quarter
- **Prediction intervals** — generating confidence intervals around forecasts (e.g., 80% confidence level) rather than single point estimates
- **Future forecasting** — applying the fitted model to synthetic future data to project revenue beyond the observed dataset

## Model Progression

1. **Model 1 (Trend only):** `Revenue = β₀ + β₁ × Time`
2. **Model 2 (Trend + Seasonality):** `Revenue = β₀ + β₁ × Time + β₂ × Dummy + β₃ × (Time × Dummy)`

Adding the dummy variable and interaction term allows the model to capture both a level shift and a slope change associated with a recurring seasonal event (e.g., a product release quarter), improving forecast accuracy over the trend-only baseline.

## Tools & Libraries

- **pandas** — data loading, filtering, and manipulation
- **NumPy** — array operations and conditional logic (dummy variable creation)
- **statsmodels** — OLS regression, model fitting, and prediction intervals
- **Matplotlib** — data visualization

## Key Takeaways

- Time series regression treats time itself as an independent variable
- Train/test splits for time series data should preserve chronological order, not be randomized
- Dummy and interaction variables are an effective way to model recurring seasonal effects in a linear framework
- Prediction intervals (not just point forecasts) are essential for communicating forecast uncertainty
- The same modeling approach used to validate against historical test data can be extended to forecast genuinely unseen future periods using synthetic input data

## Files

- `notebook.ipynb` — full analysis, from data import through future forecasting
- `qSales_2024.csv` — quarterly sales data (input)
- `synthetic_data.csv` — synthetic future periods used for out-of-sample forecasting

---
*This project was completed as part of coursework in Data Analytics (AFM 244) at the University of Waterloo.*
