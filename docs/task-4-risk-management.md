# Task 4 — Managing Risk Across Market Trade Units

[← Back to README](../README.md) · [← Previous: Task 3](task-3-hedging-securities.md)

## Scenario

Building on the securities work from Task 3, Raj and Sarah ask me to focus on **risk management**: assessing the risk exposure of Citi's market trade units and implementing strategies to protect the firm from losses while optimizing performance.

> "We're entrusted with safeguarding Citi's interests amid the volatility of the financial landscape." — **Raj**, Quantitative Analyst

## Learning Objectives

- Principles of risk management in financial markets.
- Tools and techniques for measuring and monitoring market risk.
- How to assess and mitigate market, credit and operational risk.

## Principles of Risk Management

### Types of Risk

| Risk type | Definition |
| --- | --- |
| **Market risk** | Losses from shifts in market prices — equities, interest rates, commodities, FX. |
| **Credit risk** | Losses from a counterparty failing to meet contractual obligations. |
| **Liquidity risk** | Inability to complete trades quickly and at a reasonable cost due to insufficient market depth. |
| **Operational risk** | Losses from failed internal processes, people, systems or external events. |

### The Risk Management Process

1. **Identification** — understand the risks faced by the organization or portfolio.
2. **Measurement** — quantify risk with statistical models, scenario analysis and stress testing.
3. **Mitigation** — reduce risk through diversification, hedging or risk limits.
4. **Monitoring & control** — continuously monitor exposure and adjust strategies.

## Tools & Techniques

| Tool | What it does |
| --- | --- |
| **Value at Risk (VaR)** | Maximum expected loss over a period at a given confidence level under normal conditions. |
| **Historical simulation** | Replays historical market moves to estimate potential losses. |
| **Monte Carlo simulation** | Generates many possible outcomes from random sampling of risk factors. |
| **Stress testing** | Subjects the portfolio to extreme but plausible scenarios. |
| **Sensitivity analysis** | Measures how changes in specific factors affect the risk profile. |

## Measuring & Monitoring Market Risk

### 1. Hedging

- **Futures contracts** lock in a purchase price for a future date:

$$F_t = S_t \cdot e^{(r+d)T}$$

- **Options contracts** give the right to buy at a specified price; the value follows Black-Scholes:

$$C = S_0 N(d_1) - X e^{-rT} N(d_2)$$

### 2. Value at Risk (VaR)

VaR estimates the maximum expected loss over a holding period at a confidence level:

$$\text{VaR} = Z_\alpha \cdot \sigma \cdot \sqrt{h} \cdot P$$

where $\sigma$ is the standard deviation of returns, $Z_\alpha$ the z-score for the confidence level, $h$ the holding period and $P$ the portfolio value.

### 3. Stress Testing & Scenario Analysis

- **Stress testing:** simulate extreme conditions (weather events, geopolitical shocks) and measure the impact on the coffee position.
- **Scenario analysis:** analyze specific scenarios, e.g., a 10% drop in coffee prices due to a surplus.

## Managing Credit Risk

Credit risk is the risk that a counterparty defaults on its obligations.

### 1. Credit Default Swaps (CDS)

Transfer counterparty default risk to a third party — insurance against default. The cost is driven by the credit spread and can be priced as the present value of expected default losses.

### 2. Credit Scoring Models

Assess the creditworthiness of suppliers and buyers using quantitative models such as logistic regression or machine learning. The **Altman Z-Score** is a classic:

$$Z = 1.2X_1 + 1.4X_2 + 3.3X_3 + 0.6X_4 + 0.999X_5$$

where $X_1 \dots X_5$ are financial ratios (working capital, retained earnings, EBIT, market value of equity and sales, each scaled by total assets).

### 3. Collateral Management

Require counterparties to post collateral (cash or securities) to reduce potential losses. The required amount can be set using margin requirements and **Potential Future Exposure (PFE)** models.

## Managing Operational Risk

Operational risk comes from failed internal processes, systems, people or external events.

1. **Process automation** — algorithmic execution and automated workflows reduce human error.
2. **Robust IT infrastructure** — cybersecurity measures and quantitative reliability assessments reduce downtime.
3. **Regular audits & compliance** — variance analysis and compliance scorecards catch weaknesses early.
4. **Training & development** — keep staff current on best practices and regulatory changes.

## Risk Mitigation Scenarios

### Scenario 1 — Hedging Market Risk

**Background:** coffee prices are expected to rise due to poor weather affecting crops.

**My answer:**
- **Long futures contracts** to lock in current prices for future purchases.
- **Call options** to cap the purchase price while retaining flexibility if prices fall.
- **VaR monitoring** to keep exposure within institutional limits.

### Scenario 2 — Credit Risk with a New Supplier

**Background:** a new supplier operates in a region with high economic volatility and default risk.

**My answer:**
- **Credit scoring** (Altman Z-Score) to assess the supplier's financial health.
- **Collateral requirements** based on PFE models to mitigate loss given default.
- **Credit Default Swaps** to transfer the default risk to a third party.

### Scenario 3 — Operational Risk in Trade Execution

**Background:** trading errors are increasing due to manual processes and inadequate systems.

**My answer:**
- **Process automation** — algorithmic trading and automated workflows.
- **IT infrastructure enhancement** — cybersecurity and system reliability assessments.
- **Continuous monitoring & auditing** — quantitative audits and variance analysis.

## Risk Management Analysis — Deliverable

**Division:** Markets and Quantitative Analysis (MQA) · **Date:** May 7, 2026

### Scenario 1 — Hedging Market Risk

*Predicted increase in coffee prices due to adverse weather conditions affecting crop yields.*

- **Futures contracts:** implement long futures positions to lock in current price levels for future deliveries, neutralizing spot price appreciation.
- **Call options strategy:** purchase calls to gain the right to buy coffee at a predetermined strike, hedging against price spikes while maintaining flexibility.
- **VaR monitoring:** quantify potential portfolio losses under normal conditions and keep exposure within institutional limits.

### Scenario 2 — Credit Risk with a New Supplier

*Onboarding a supplier from a region with high economic volatility and default risk.*

- **Credit Default Swaps:** transfer counterparty default risk to a third party for financial compensation in case of non-performance.
- **Quantitative credit scoring:** apply the Altman Z-Score to evaluate the supplier's financial health and probability of default.
- **Collateral management:** mandate collateral (cash or securities) based on PFE models to mitigate loss given default.

### Scenario 3 — Operational Risk in Trade Execution

*Increase in trading errors attributed to manual processes and inadequate systems.*

- **Process automation:** deploy algorithmic trading systems and automated workflows to minimize human error.
- **IT infrastructure enhancement:** robust cybersecurity and quantitative system reliability assessments to reduce downtime.
- **Continuous monitoring & auditing:** regular quantitative audits and variance analysis to ensure compliance and catch weaknesses early.

### Conclusion

By integrating market, credit and operational risk mitigation strategies, the MQA division ensures informed decision-making and optimal performance in a volatile market landscape.

## Key Takeaways

- Risk management is a cycle: identify, measure, mitigate, monitor — then repeat.
- Market, credit and operational risks each need a different toolkit (hedges/VaR, CDS/scoring/collateral, automation/audits).
- VaR is useful but incomplete; stress testing and Expected Shortfall capture tail risk that VaR misses.
- The goal is not to eliminate risk but to keep it within limits the firm understands and can survive.

---

[← Previous: Task 3](task-3-hedging-securities.md) · [Back to README](../README.md)
