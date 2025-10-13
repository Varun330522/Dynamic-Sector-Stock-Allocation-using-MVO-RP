
# NIFTY Sector and Stock Level Portfolio Optimization

## Project Objective

This project compares the performance of two portfolio optimization strategies – a two-level Mean-Variance Optimization (MVO) and a two-level Risk Parity (RP) – against the NIFTY50 benchmark index. The goal is to evaluate how these strategies perform using a universe of NIFTY sector indices and selected stocks within those sectors.

## Data

The analysis uses historical daily closing price data downloaded from Yahoo Finance (`yfinance`). The data includes:

-   **NIFTY Sector Indices:** NIFTY IT, NIFTY PHARMA, NIFTY AUTO, NIFTY ENERGY, and NIFTY BANK.
-   **Selected Stocks:** A basket of 5 stocks from each of the above NIFTY sectors.
-   **Benchmark:** NIFTY50 (`^NSEI`).

The data covers the period from **2020-01-01** to the latest available date.

## Methodology: Two-Level Optimization

Both MVO and Risk Parity strategies are implemented using a two-level approach:

1.  **Sector Level:** Allocate weights across the chosen NIFTY sectors.
2.  **Stock Level:** Allocate weights to individual stocks *within* the sectors selected in the first level.

Portfolios are rebalanced every **63** trading days, using a lookback window of **100** trading days to calculate expected returns and covariance matrices.

### Mean-Variance Optimization (MVO)

-   **Sector Level:** Selects the top **3** sectors based on a hybrid score (combining mean return, momentum, and Sharpe proxy). MVO is then applied to these top sectors to determine sector weights.
-   **Stock Level:** Within each selected sector, MVO is applied to the constituent stocks to determine their weights.
-   **Constraints:** A constraint of 40% maximum weight per individual stock is applied to prevent overconcentration. An L1 turnover penalty is also included in the objective function to manage trading costs.

### Risk Parity (RP)

-   **Sector Level:** Allocates weights to all available sectors based on the principle of equal risk contribution.
-   **Stock Level:** Within each sector, allocates weights to constituent stocks based on the principle of equal risk contribution.

## Performance Metrics

The performance of the strategies (Gross and Net of transaction costs) and the benchmark is evaluated using the following annualized metrics:

-   Annualized Return
-   Annualized Volatility
-   Sharpe Ratio
-   Sortino Ratio
-   Max Drawdown
-   Calmar Ratio
-   CAGR (Geometric)

## Transaction Costs

Transaction costs (set at **0.25%​** per trade) are also considered in the analysis.

