# Task 3 — Hedging & Structuring Securities

[← Back to README](../README.md) · [← Previous: Task 2](task-2-coffee-futures.md)

## Scenario

Building on the pricing analysis from Task 2, Raj and Sarah ask me to develop **hedging strategies** to mitigate risk and **structure securities products** tailored to our clients' needs.

> "Our clients are counting on us to navigate the volatile coffee market and shield them from potential risks. It's up to us to craft innovative solutions that not only safeguard their investments but also capitalize on emerging opportunities." — **Sarah**, Quantitative Analyst

## Learning Objectives

- Strategies for hedging financial risks using derivative instruments.
- Techniques for structuring securities to meet client needs.
- How to match a product to a client's risk profile.

## Hedging with Derivative Instruments

### 1. Options Contracts

Options give the holder the right — but not the obligation — to buy or sell an asset at a predetermined strike price within a specified period.

- **Protect against a price decline:** buy **put options** to establish a minimum selling price. If coffee trades at \$1.20/lb, a put with a \$1.15 strike lets you sell at \$1.15 even if the market falls below that level.
- **Protect against a price increase:** buy **call options** to lock in a purchase price while retaining upside flexibility.
- **Generate income:** sell a **covered call**, capping upside in exchange for premium.

### 2. Options Strategies

| Strategy | Use case |
| --- | --- |
| **Long put** | Protect against downside price moves. |
| **Long call** | Hedge against price spikes while keeping flexibility. |
| **Covered call** | Generate income, cap upside. |
| **Straddle** | Profit from large moves in either direction. |
| **Collar** | Combine a put and a call to bound the price range while managing cost. |

### 3. Hedging with Swaps

Swaps are agreements between two parties to exchange cash flows, typically to hedge interest-rate or currency risk. While more common in rates and FX, they can stabilize the financing costs of coffee production or inventory and therefore indirectly support the options book.

### 4. Risk Management Considerations

Effective hedging requires weighing costs, benefits and risks, and tailoring strategies to the client. In highly volatile markets, a **collar** can offer protection against large swings while keeping the cost of options manageable. Continuous monitoring and adjustment are essential.

## Knowledge Checks

**Q1 — Which strategy best protects against downside risk if prices are expected to fall?**
> **Purchasing put options.** A put gives the right to sell at the strike price, establishing a minimum selling price.

**Q2 — When would a quant use interest rate swaps when pricing coffee futures?**
> **When there is a strong positive correlation between coffee prices and interest rates.** Swaps hedge the financing costs of production and storage, which feed into futures pricing.

**Q3 — Which risk management consideration is essential when implementing hedging strategies?**
> **Monitoring market developments and adjusting strategies accordingly.** Hedges must evolve with market conditions and client objectives.

## Structuring Securities

Structuring creates financial products with specific risk-return profiles tailored to investor needs.

### 1. Commodity-Linked Bonds

Bonds whose return is linked to a commodity price such as coffee.

$$P_b = P_f + \lambda \Delta C$$

where $P_b$ is the bond price, $P_f$ the fixed interest component, $\lambda$ the sensitivity to coffee prices and $\Delta C$ the change in coffee prices.

**Best for:** clients who want coffee exposure without trading commodities directly.

### 2. Exchange-Traded Funds (ETFs)

Funds traded on exchanges that hold assets such as coffee futures.

- **Portfolio construction:** optimization algorithm to build a diversified basket of coffee futures with minimal risk for the target exposure.
- **Tracking error:** measure how closely the ETF follows its benchmark:

$$TE = \sqrt{\frac{1}{n}\sum_{t=1}^{n}\left(R_{p,t} - R_{b,t}\right)^2}$$

**Best for:** clients seeking easy, diversified access to coffee prices.

### 3. Structured Notes

Debt securities whose return is linked to a commodity index or price.

$$P_n = F + \alpha\left(C_T - C_0\right)$$

where $P_n$ is the note price, $F$ the fixed component, $\alpha$ the participation rate, $C_T$ the coffee price at maturity and $C_0$ the initial coffee price.

- **Risk assessment:** Monte Carlo simulation to model the range of outcomes and calibrate the participation rate.

**Best for:** clients who want income plus exposure to coffee movements.

### 4. Digital Options

Options that pay a fixed amount if the underlying meets a condition at expiration.

- **Digital call:** pays 1 if the asset price is above the strike at expiration.
- **Digital put:** pays 1 if the asset price is below the strike at expiration.
- **Pricing:** use the binary option pricing formula and scenario analysis to estimate the probability of each outcome.

**Best for:** high-risk investors who want a leveraged, binary payoff.

## Client Scenarios

| Client profile | Goal | Recommended product | Quantitative implementation |
| --- | --- | --- | --- |
| **Conservative investor** | Stable returns with limited coffee exposure | **Commodity-linked bonds** | Bond pricing model to set sensitivity $\lambda$ and the fixed rate. |
| **Moderate risk taker** | Income plus coffee exposure | **Structured notes** | Payoff $P_n = F + \alpha(C_T - C_0)$; Monte Carlo to calibrate $\alpha$. |
| **High-risk investor** | Large payoff from significant price moves | **Digital options** | Binary pricing formula plus scenario analysis. |
| **Diversification seeker** | Easy access to coffee price movements | **ETFs** | Portfolio optimization; tracking-error measurement. |

## Example Answer — High-Risk Investor

**Situation:** a high-risk investor wants a product that pays significantly if coffee prices rise sharply over the next six months.

**Recommendation:** **digital call options** on coffee that pay a fixed amount if prices exceed a specified level within six months.

- **Pricing:** apply the binary option pricing formula and scenario analysis to estimate the probability of different outcomes.
- **Strike and premium:** use the coffee pricing model from Task 2 to set the strike and premium, accounting for volatility and historical data.

**Why it fits:** digital calls deliver the high-risk, high-reward profile the investor is looking for, while the pricing model ensures the product is fairly valued.

## Key Takeaways

- Hedging is about choosing the right instrument for the risk — puts for downside, calls for upside, collars for both.
- Structuring translates a client's risk appetite into a concrete payoff profile.
- The same pricing toolkit (cost of carry, Black-Scholes, Monte Carlo) underpins both hedging and structuring.
- Product design is as much about client objectives as it is about mathematics.

---

[← Previous: Task 2](task-2-coffee-futures.md) · [Back to README](../README.md) · [Next: Task 4 →](task-4-risk-management.md)
