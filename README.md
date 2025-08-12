# Time Series Forecasting Project – TSLA, BND, SPY

## Overview
This project analyzes historical financial data for **Tesla (TSLA)**, **Vanguard Total Bond Market ETF (BND)**, and **SPDR S&P 500 ETF Trust (SPY)** to identify trends, volatility, and anomalies.  
It applies **time series forecasting** to Tesla’s stock price using classical statistical and deep learning approaches.

---

## Objectives
1. **Data Understanding & Cleaning** – Load, inspect, and preprocess historical OHLCV data.  
2. **Exploratory Data Analysis (EDA)** – Examine trends, volatility, and stationarity.  
3. **Forecasting** – Implement ARIMA/SARIMA and LSTM models to predict Tesla’s future stock prices.  
4. **Model Evaluation** – Compare models based on error metrics and interpret results.

---

## Methodology

### **Task 1: Data Understanding, Cleaning & EDA**
- **Data Extraction**  
  - Downloaded OHLCV data (2015–2025) for TSLA, BND, SPY from Yahoo Finance using `yfinance`.  
  - Flattened multi-index columns for easier handling.

- **Data Preprocessing**  
  - Checked for missing values and handled appropriately.  
  - Calculated rolling volatility (30-day standard deviation, annualized).  
  - Saved cleaned close prices to `../data/close_prices_clean.csv`.

- **EDA**  
  - Summary statistics for all securities.  
  - Plotted historical closing prices to visualize trends.  
  - Calculated and visualized daily returns to assess volatility.  
  - Performed Augmented Dickey-Fuller (ADF) test for stationarity.  
  - Identified periods with unusually high or low returns.

---

### **Task 2: Time Series Forecasting**
- **Data Preparation**  
  - Loaded `close_prices_clean.csv`.  
  - Focused on Tesla’s closing prices (`TSLA`).  
  - Chronological split:  
    - **Training set:** 2015-01-01 to 2023-12-31  
    - **Test set:** 2024-01-01 to 2025-08-09  

- **Modeling Approaches**  
  1. **ARIMA/SARIMA** – Classical statistical forecasting model.  
     - Parameter tuning using grid search / `auto_arima`.  
  2. **LSTM** – Deep learning model for sequential data.  
     - Tuned architecture, epochs, and batch size.

- **Evaluation Metrics**  
  - **MAE** – Mean Absolute Error  
  - **RMSE** – Root Mean Squared Error  
  - **MAPE** – Mean Absolute Percentage Error  

- **Outcome**  
  - Compared forecast accuracy between ARIMA/SARIMA and LSTM.  
  - Discussed trade-offs in model complexity, interpretability, and performance.

---

## Tools & Libraries
- **Python 3.x**  
- **pandas**, **numpy** – Data manipulation  
- **matplotlib**, **seaborn** – Visualization  
- **yfinance** – Financial data extraction  
- **statsmodels** – Statistical tests & ARIMA modeling  
- **scikit-learn** – Metrics & preprocessing  
- **tensorflow / keras** – LSTM deep learning modeling

---
