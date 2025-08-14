# Time Series Forecasting & Portfolio Optimization – TSLA, BND, SPY

## 📌 Overview
This project performs a full end-to-end **financial time series analysis** of three assets:

- **Tesla (TSLA)** – high-growth, high-volatility stock.
- **Vanguard Total Bond Market ETF (BND)** – stable fixed-income asset.
- **SPDR S&P 500 ETF Trust (SPY)** – broad U.S. equity market benchmark.

-Explored historical trends, build and compare forecasting models, optimize a portfolio using **Modern Portfolio Theory (MPT)**, and backtest the strategy against a benchmark.

---

## 🎯 Objectives
1. **Data Understanding & Cleaning** – Extract, inspect, and prepare historical price data.
2. **Exploratory Data Analysis (EDA)** – Visualize and interpret asset trends, volatility, and relationships.
3. **Forecasting** – Predict Tesla’s stock price using ARIMA/SARIMA and LSTM models.
4. **Portfolio Optimization** – Use forecasts to construct an optimal TSLA–BND–SPY portfolio.
5. **Backtesting** – Evaluate the strategy against a benchmark portfolio.

---

## 🛠 Methodology & Tasks

### **Task 1 – Data Understanding, Cleaning & EDA**
- **Data Collection:** Downloaded OHLCV data (2015–2025) from Yahoo Finance with `yfinance`.
- **Preprocessing:**  
  - Flattened multi-index columns.  
  - Checked for missing values and corrected where needed.  
  - Calculated daily returns and rolling 30-day annualized volatility.
- **Exploration:**  
  - Summary statistics for each asset.  
  - Price and return plots to visualize trends and volatility cycles.  
  - Augmented Dickey-Fuller (ADF) test for stationarity.
- **Outcome:**  
  - Clean dataset saved as `close_prices_clean.csv` for modeling.

---

### **Task 2 – Time Series Forecasting**
- **Focus:** Forecast **TSLA** closing prices.
- **Data Split:**  
  - Train: 2015-01-01 → 2023-12-31  
  - Test: 2024-01-01 → 2025-08-09
- **Models Implemented:**  
  1. **ARIMA/SARIMA** – Statistical time series approach with grid search tuning.  
  2. **LSTM** – Deep learning model for sequential data with tuned architecture.
- **Evaluation Metrics:**  
  - Mean Absolute Error (MAE)  
  - Root Mean Squared Error (RMSE)  
  - Mean Absolute Percentage Error (MAPE)
- **Outcome:**  
  - Compared ARIMA/SARIMA vs LSTM performance.  
  - Visualized test forecasts with actuals.  
  - Selected best-performing model for forward forecasts.

---

### **Task 3 – Forecast Future Market Trends**
- Used the best-performing model (LSTM) to forecast **6–12 months of TSLA prices**.
- Plotted forecast alongside historical prices.
- Included **confidence intervals** to indicate uncertainty.
- Interpreted the projected trend and potential market risks.

---

### **Task 4 – Portfolio Optimization (MPT)**
- Assets: **TSLA (forecasted returns)**, **BND (historical average return)**, **SPY (historical average return)**.
- **Covariance Matrix:** Calculated from historical daily returns.
- Generated **Efficient Frontier** showing optimal risk-return tradeoffs.
- Identified:  
  - **Maximum Sharpe Ratio Portfolio** (Tangency Portfolio)  
  - **Minimum Volatility Portfolio**
- **Final Recommendation:**  
  - Provided optimal weights for TSLA, BND, SPY.  
  - Reported expected annual return, volatility, and Sharpe Ratio.  
  - Explained reasoning behind portfolio choice (risk-adjusted return focus).

---

### **Task 5 – Strategy Backtesting**
- **Backtest Period:** 2024-08-01 → 2025-07-31.
- **Benchmark:** 60% SPY / 40% BND static portfolio.
- **Simulation:**  
  - Applied Task 4’s optimal weights to historical price data.  
  - Compared cumulative returns to benchmark.  
  - Calculated Sharpe Ratios and annualized returns.
- **Outcome:**  
  - Visualized performance comparison.  
  - Evaluated if the strategy outperformed the benchmark in return and risk-adjusted terms.  
  - Discussed limitations (e.g., no monthly rebalancing, single-model dependency).

---

## 📚 Tools & Libraries
- **Python 3.x**  
- Data Handling: `pandas`, `numpy`  
- Visualization: `matplotlib`, `seaborn`  
- Financial Data: `yfinance`  
- Modeling: `statsmodels` (ARIMA/SARIMA), `tensorflow/keras` (LSTM)  
- Metrics: `scikit-learn`

---

## 📈 Key Insights
- TSLA’s volatility is substantially higher than BND and SPY.
- LSTM model provided more accurate short-term forecasts compared to ARIMA/SARIMA.
- MPT optimization suggested a diversified mix to balance TSLA’s high growth potential with stability from bonds and index funds.
- Backtesting indicated that the optimized portfolio could outperform a traditional 60/40 mix, though further robustness testing is required.
