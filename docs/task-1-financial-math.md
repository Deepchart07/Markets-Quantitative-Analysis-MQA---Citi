# Task 1 — Financial Math Fundamentals & Team Structure

[← Back to README](../README.md)

## Scenario

I join Citi's Markets division as a **quantitative analyst intern** for the summer. My role is to assist the Markets Quant team with quantitative analysis, learning from experienced mentors and contributing to live projects.

> "Your goal is to actively contribute to the team's projects by completing tasks that range from reviewing financial math fundamentals to pricing commodities, hedging securities, and managing risk." — **Aisha**, Senior Quantitative Analyst

## Learning Objectives

- Key mathematical concepts essential for quantitative analysis in financial markets.
- Mathematical modeling techniques for pricing commodities, structuring securities and managing risk.
- Essential calculus, linear algebra and stochastic calculus for financial analysis.
- The structure and roles within Citi's Markets Quant team.

## The Team

| Member | Role |
| --- | --- |
| **Edward Rosales** | Quantitative Analyst Intern |
| Aisha | Senior Quantitative Analyst — Manager |
| Raj | Quantitative Analyst — Colleague |
| Rae | Quantitative Analyst — Colleague (forecasting & Python) |
| Sarah | Quantitative Analyst — Colleague (risk management) |

## Asset Classes at Citi

| Asset class | What it covers |
| --- | --- |
| **Equities** | Physical shares, ETFs, synthetic shares, baskets, options and other derivatives. |
| **Cash Equities** | Market access through sales trading, program trading and electronic trading. |
| **Prime Services** | Cross-asset financing, securities lending, analytics, advisory, listed execution and derivatives clearing. |
| **Derivatives Markets** | Equity options, swaps, warrants, structured notes, futures and custom indices/baskets. |
| **Commodities** | Customized solutions to manage volatility; physical and financial commodities. |
| **FX** | 130 currencies and ~80 countries; hedging, international investments and market views. |
| **Rates** | Sovereign/agency securities, interest rate derivatives, structured notes, secured financing. |
| **Credit** | Corporate and EM bonds, ABS/MBS, CLOs, municipal and agency securities, loans, derivatives. |

## Handling Different Asset Classes

| Asset class | Typical quantitative approach |
| --- | --- |
| Equities | Linear regression for price moves; volatility & factor models; portfolio optimization. |
| Fixed Income | Interest-rate modeling; duration & convexity; yield-curve analysis. |
| Commodities | Supply/demand forecasting; futures hedging; options for flexible strategies. |
| Currencies | FX forecasting models; forwards & options; geopolitical/economic analysis. |
| Derivatives | Black-Scholes pricing; Monte Carlo; delta-hedging. |
| Real Estate | DCF valuation; market comparables; risk factor assessment. |
| Alternative Investments | Sharpe ratio & alpha; private equity screening; stress testing. |

## Knowledge Check — Asset Class Analysis

**Prompt:** Explain how you would approach analyzing and managing an investment in one of these asset classes. Describe the key factors, the quantitative methods and how you would apply them to manage risk and optimize returns.

**My answer — Equities:**

- **Key factors:** factor exposure (value, momentum, quality) and systematic risk (beta). Institutional flows and liquidity are critical in high-volatility regimes.
- **Quantitative methods:**
  - **Multifactor models** (Fama-French) to isolate alpha from market returns.
  - **Mean-variance optimization / efficient frontier** to maximize risk-adjusted returns using covariance matrices.
  - **Python-based backtesting** to validate strategy robustness.
- **Risk & optimization:** volatility-based position sizing, daily **VaR** and **stress testing** for black-swan events — maximizing the Sharpe ratio while preserving capital.

## Mathematical Foundations

### Probability & Statistics

- **Probability theory:** random variables, distributions (normal, binomial, Poisson), expected value, conditional probability and Bayes' theorem.
- **Statistical inference:** hypothesis testing, confidence intervals, p-values and the central limit theorem.
- **Applications:** risk assessment (VaR / CVaR), regression analysis and Monte Carlo simulation.

> **Example:** to price a complex derivative, use Monte Carlo to generate a range of possible future asset prices, compute the derivative's payoff on each simulated path and average the results.

### Calculus & Differential Equations

- **Differential calculus:** derivatives and partial derivatives measure rates of change.
- **Integral calculus:** accumulation of quantities and areas under curves.
- **Differential equations:** ODEs and PDEs describe how quantities change over time (e.g., the Black-Scholes PDE).
- **Applications:** Black-Scholes option pricing and stochastic differential equations (SDEs) for asset prices.

The Black-Scholes formula for a European call option:

$$C = S_0 N(d_1) - X e^{-rT} N(d_2)$$

$$d_1 = \frac{\ln(S_0/X) + \left(r + \tfrac{1}{2}\sigma^2\right)T}{\sigma\sqrt{T}}, \qquad d_2 = d_1 - \sigma\sqrt{T}$$

where $N(\cdot)$ is the cumulative distribution function of the standard normal distribution.

### Mathematical Modeling

- **Linear models:** multiple regression and factor models.
- **Time series:** ARIMA and GARCH for trends, seasonality and volatility clustering.
- **Stochastic processes:** Brownian motion and geometric Brownian motion (GBM).
- **Monte Carlo methods** and **risk-neutral valuation**.

> **Example:** fit an ARIMA model to historical commodity prices to forecast future movements and hedge against price volatility.

## Knowledge Check — Coffee Commodity Scenario

**Prompt:** As a summer quant analyst working with coffee commodities, explain the mathematics you would use to (1) price a futures contract, (2) structure a security, and (3) manage risk.

**My answer:**

### 1. Pricing a futures contract — Cost of Carry

I would use the **cost of carry model**, and go beyond the math to focus on the **convenience yield**. If there is a supply shock (e.g., bad weather in Brazil), the convenience yield spikes and the market shifts into **backwardation**. My role is to price that "hunger" for physical coffee into the contract so the desk is not arbitrageable.

$$F_t = S_t \cdot e^{(r+d)T}$$

where $F_t$ is the futures price, $S_t$ the spot price, $r$ the risk-free rate, $d$ the storage cost and $T$ the time to maturity.

### 2. Structuring securities — Capital Protected Note

I would build a **capital protected note**: invest the bulk of the funds in a **zero-coupon bond** to guarantee principal, and use the remaining yield to buy an **Asian call option**. The Asian (average-price) style smooths coffee's high volatility and makes the product cheaper for the client.

### 3. Risk management — Fat tails

I look past standard deviations and focus on fat tails:

- **Expected Shortfall (CVaR):** the expected loss in the worst 5% of cases, not just the average day.
- **GARCH models:** detect volatility clustering and signal the desk to trim positions when the market gets jumpy.
- **Stress testing:** "what-if" scenarios (e.g., a 20% port shutdown) to make sure a single event cannot blow up the book.

## Example Answer

**Pricing a futures contract:** use the cost of carry model to relate the futures price to the spot price, storage costs and the risk-free rate:

$$F_t = S_t \cdot e^{(r+d)T}$$

**Structuring securities:** use linear regression to quantify the relationship between coffee prices and economic factors, and geometric Brownian motion to simulate future price paths and design the payout.

**Managing risk:** combine **VaR** (maximum expected loss at a confidence level), **Monte Carlo simulation** (distribution of future prices) and **GARCH** (volatility forecasting).

## Key Takeaways

- Asset classes differ in liquidity, risk drivers and the quantitative toolkit they require.
- Probability, calculus and modeling are the foundation of every pricing and risk decision.
- In commodities, the physical market (supply shocks, convenience yield, backwardation) matters as much as the formula.
- A structured product is a risk-management decision expressed as a financial instrument.

---

[← Back to README](../README.md) · [Next: Task 2 →](task-2-coffee-futures.md)
