# Market Portfolio Risk Analysis

## Project Overview

This project analyzes the historical performance and risk characteristics
of three hypothetical investment portfolios using real market data.

The analysis uses four ETFs:

- **SPY** — S&P 500 exposure
- **QQQ** — Nasdaq-100 exposure
- **TLT** — Long-term U.S. Treasury exposure
- **GLD** — Gold exposure

The dataset covers daily market observations from **January 2019 through
December 2025**.

Three portfolios were constructed to represent different risk profiles:

| Portfolio | SPY | QQQ | TLT | GLD |
|---|---:|---:|---:|---:|
| Conservative | 40% | — | 40% | 20% |
| Balanced | 60% | — | 30% | 10% |
| Growth | 40% | 50% | 10% | — |

The project evaluates these portfolios using both performance and
risk-management metrics.

### Key Metrics

- Annualized Return
- Annualized Volatility
- Sharpe Ratio
- Sortino Ratio
- Beta
- Treynor Ratio
- Jensen's Alpha
- Historical Value at Risk (VaR)
- Expected Shortfall (ES)
- Maximum Drawdown
- Rolling Volatility
- Stress-period returns

The final analysis is presented through Python/Jupyter notebooks and an
Excel-based portfolio dashboard.

## Project Objective

The objective is to examine the relationship between **return, volatility,
market exposure, downside risk, and risk-adjusted performance** across
different portfolio constructions.

The project emphasizes evaluating portfolios using multiple measures rather
than relying on historical return alone.

## Tools & Technologies

- Python
- Pandas
- NumPy
- yfinance
- Matplotlib
- Jupyter Notebook
- OpenPyXL
- Microsoft Excel
- Git/GitHub

## Project Structure

```text
market-portfolio-risk-analysis/
│
├── README.md
│
├── notebooks/
│   ├── 01_data_collection.ipynb
│   ├── 02_portfolio_construction.ipynb
│   ├── 03_performance_ratios.ipynb
│   ├── 04_risk_analytics.ipynb
│   ├── 05_decision_dashboard.ipynb
│   └── 06_final_report.ipynb
│
├── data/
│   ├── raw/
│   └── processed/
│
├── reports/
│   └── portfolio_analysis.xlsx
│
└── src/


### Next: Methodology & Workflow

Paste this **below** the closing ```:

```markdown
## Methodology & Workflow

The project follows a structured portfolio risk-analysis workflow:

**Market Data → Data Validation → Daily Returns → Portfolio Construction → Performance Analysis → Risk Analytics → Stress Testing → Decision Dashboard**

### 1. Market Data Collection

Historical daily adjusted prices were collected for SPY, QQQ, TLT and GLD
using `yfinance`.

The analysis period covers **January 2019 through December 2025**.

### 2. Portfolio Construction

Three hypothetical portfolios were constructed using predefined asset
weights:

- **Conservative:** 40% SPY, 40% TLT, 20% GLD
- **Balanced:** 60% SPY, 30% TLT, 10% GLD
- **Growth:** 40% SPY, 50% QQQ, 10% TLT

Daily portfolio returns were calculated using the weighted returns of the
underlying assets.

### 3. Performance Analysis

Portfolio performance was evaluated using:

- Annualized Return
- Annualized Volatility
- Sharpe Ratio
- Sortino Ratio
- Beta
- Treynor Ratio
- Jensen's Alpha

### 4. Risk Analytics

The project measures portfolio downside and tail risk using:

- Historical VaR at the 95% confidence level
- Expected Shortfall at the 95% confidence level
- Maximum Drawdown
- 30-trading-day Rolling Volatility

### 5. Stress Testing

Portfolio performance was examined across two selected historical periods:

- **February–June 2020**
- **Calendar year 2022**

### 6. Reporting

The final results are consolidated into an Excel portfolio dashboard and
a final Jupyter Notebook containing the quantitative analysis and
interpretation.

## Key Findings

The analysis produced the following historical results:

| Portfolio | Annualized Return | Annualized Volatility | Sharpe Ratio | Beta | Max Drawdown |
|---|---:|---:|---:|---:|---:|
| Conservative | 10.50% | 10.81% | 0.972 | 0.369 | -25.07% |
| Balanced | 12.32% | 12.60% | 0.978 | 0.573 | -24.90% |
| Growth | 18.73% | 19.60% | 0.956 | 0.962 | -30.31% |

### Observations

- The **Growth portfolio** generated the highest annualized historical
  return at **18.73%**, but also had the highest annualized volatility
  at **19.60%**.
- The Growth portfolio had the highest beta at **0.962**, indicating
  greater sensitivity to movements in the S&P 500 than the other two
  portfolios.
- The **Conservative portfolio** had the lowest annualized volatility
  at **10.81%** and the lowest beta at **0.369**.
- The **Balanced portfolio** recorded the highest Sharpe Ratio at
  approximately **0.978**.
- The **Conservative portfolio** recorded the highest Sortino Ratio at
  approximately **1.587**.
- The Growth portfolio experienced the largest maximum drawdown at
  **-30.31%**.
- The results demonstrate that a higher historical return does not
  necessarily correspond to stronger risk-adjusted performance.

### Tail Risk

At the 95% historical confidence level:

| Portfolio | Historical VaR | Expected Shortfall |
|---|---:|---:|
| Conservative | -1.05% | -1.54% |
| Balanced | -1.16% | -1.86% |
| Growth | -1.83% | -2.93% |

The Growth portfolio recorded the largest historical VaR and Expected
Shortfall, indicating greater observed daily downside exposure in the
sample.

### Stress-Period Results

| Portfolio | 2020 Selected Stress Period | 2022 Annual Return |
|---|---:|---:|
| Conservative | 8.48% | -19.73% |
| Balanced | 5.23% | -19.95% |
| Growth | 7.51% | -26.54% |

These results represent selected historical periods rather than forecasts
of future performance.

## Limitations & Methodology Notes

The results in this project are historical estimates and should not be
interpreted as forecasts or guarantees of future performance.

### Annualized Return

Annualized return is calculated as:

**Mean Daily Return × 252**

This represents an annualized arithmetic return estimate and is **not CAGR**.

### Annualized Volatility

Annualized volatility is calculated as:

**Daily Standard Deviation × √252**

### Risk-Free Rate

The Sharpe Ratio, Treynor Ratio and Jensen's Alpha calculations in this
project assume a **0% risk-free rate**.

### Sortino Ratio

The current implementation uses a simplified downside-deviation approach
based on portfolio returns clipped at zero. A more conventional
implementation can use only returns below a specified target or minimum
acceptable return.

### Beta

Portfolio beta is calculated relative to **SPY** using:

**Covariance(Portfolio, SPY) ÷ Variance(SPY)**

### Jensen's Alpha

Jensen's Alpha is calculated using the simplified zero-risk-free-rate
form:

**Portfolio Return − (Beta × Benchmark Return)**

### Historical VaR and Expected Shortfall

Historical VaR and Expected Shortfall are backward-looking measures based
on the observed return distribution in the sample period. Results can vary
depending on the historical window, confidence level and market conditions.

### Stress Testing

The stress analysis uses selected historical windows and is intended to
illustrate portfolio behavior under different market environments. The
2020 and 2022 periods have different durations and therefore should not be
treated as directly comparable crisis windows.

### Portfolio Weights

The portfolio allocations are hypothetical and are used for analytical
purposes. They do not represent personalized investment advice or an
actual client portfolio.

## How to Run the Project

### 1. Clone the Repository

```bash
git clone <your-github-repository-url>
cd market-portfolio-risk-analysis
```

### 2. Install the Required Python Packages

```bash
pip install -r requirements.txt
```

### 3. Run the Notebooks

Run the notebooks in the following order:

1. `01_data_collection.ipynb`
2. `02_portfolio_construction.ipynb`
3. `03_performance_ratios.ipynb`
4. `04_risk_analytics.ipynb`
5. `05_decision_dashboard.ipynb`
6. `06_final_report.ipynb`

Each notebook builds on outputs generated by the previous stage.

### 4. Review the Final Outputs

The main outputs are:

- Processed portfolio and risk datasets in `data/processed/`
- Final Excel portfolio dashboard in `reports/portfolio_analysis.xlsx`
- Final analytical interpretation in `06_final_report.ipynb`