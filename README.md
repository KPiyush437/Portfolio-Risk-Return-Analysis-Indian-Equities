# Portfolio Risk & Return Analysis — Indian Equities

## Objective

The goal of this project is to construct and evaluate an equal-weighted stock portfolio of large-cap Indian equities and compare its risk-adjusted performance against the Nifty 50 index benchmark. Specifically, the analysis aims to quantify portfolio volatility, assess diversification benefits, and visualize cumulative return trajectories over a multi-year horizon (2013–2022).

---

## Dataset Attributes

Historical daily closing prices were sourced via the **Yahoo Finance API (`yfinance`)** for the following instruments:

| Ticker | Company |
|---|---|
| `TCS.NS` | Tata Consultancy Services |
| `HDFCBANK.NS` | HDFC Bank |
| `BHARTIARTL.NS` | Bharti Airtel |
| `MARUTI.NS` | Maruti Suzuki |
| `NESTLEIND.NS` | Nestlé India |
| `^NSEI` | Nifty 50 Index (benchmark) |

- **Date range:** January 1, 2013 – December 31, 2022
- **Frequency:** Daily closing prices (auto-adjusted for splits and dividends)
- **Derived features:** Daily percentage returns, covariance matrix, cumulative return series

---

## Methodology

1. **Return Calculation** — Daily returns computed using percentage change on adjusted closing prices; the first row dropped (`dropna()`).

2. **Portfolio Construction** — An equal-weighted portfolio was formed with weights of **20% per stock** (weights sum to 1).

3. **Volatility Estimation**
   - *Individual stock volatility:* annualized by multiplying daily standard deviation by √252.
   - *Portfolio variance:* computed via the quadratic form **wᵀ Σ w**, where Σ is the sample covariance matrix of daily returns.
   - *Annual portfolio volatility:* portfolio variance scaled by 252, then square-rooted.

4. **Benchmark Comparison** — The Nifty 50 index served as a market proxy. Cumulative returns for both the portfolio and the index were computed as the running product of (1 + daily return).

5. **Visualization** — Cumulative return series plotted on a shared axis to enable direct performance comparison.

---

## Key Findings

### Individual Stock Volatilities (Annualized)

| Stock | Annualized Volatility |
|---|---|
| Bharti Airtel | 31.98% |
| Maruti Suzuki | 29.41% |
| Nestlé India | 23.92% |
| TCS | 24.67% |
| HDFC Bank | 23.75% |

### Portfolio-Level Risk

| Metric | Value |
|---|---|
| Daily Portfolio Variance | 0.000110 |
| Annual Portfolio Variance | 0.027755 |
| **Annual Portfolio Volatility** | **16.66%** |

The portfolio volatility of **16.66%** is meaningfully lower than each constituent stock's individual volatility (ranging from ~24% to ~32%), demonstrating the **diversification benefit** of combining imperfectly correlated assets.

### Cumulative Return Performance

As shown in the chart, the equal-weighted portfolio generated a cumulative return of approximately **~6×** over the 10-year period (2013–2022), significantly outperforming the Nifty 50 benchmark, which returned roughly **~3×** over the same period. The portfolio's outperformance is particularly pronounced post-2020, likely driven by strong recoveries in technology (TCS) and telecom (Bharti Airtel) sectors.

![Cumulative Returns]("C:\Users\DELL\OneDrive\Pictures\Screenshots\Screenshot 2026-02-24 230158.png")

> **Note:** Past performance does not guarantee future results. This analysis is for educational purposes only.
