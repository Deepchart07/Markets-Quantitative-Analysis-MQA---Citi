# Task 2 — Pricing Commodities: Coffee Futures

[← Back to README](../README.md) · [← Previous: Task 1](task-1-financial-math.md)

## Scenario

Another day as a quantitative summer analyst at Citi. This morning the team meets to discuss the complexities of **commodity pricing**, focusing specifically on **coffee futures contracts**.

My task is to price coffee futures by analyzing market data and applying quantitative methods to determine fair prices, while evaluating how supply and demand, weather patterns and geopolitical factors influence those prices.

> "Pricing these contracts accurately is crucial for managing risk and making informed trading decisions." — **Aisha**, Senior Quantitative Analyst

## Learning Objectives

- Techniques for pricing commodities in financial markets.
- Factors influencing the pricing of coffee futures contracts.
- How to apply the cost of carry, Black-Scholes and Monte Carlo models in practice.

## Futures Contracts & Price Drivers

A **futures contract** is a standardized agreement traded on an exchange, where the buyer agrees to purchase a specific quantity of a good at a predetermined price on a future date.

| Driver | What to watch |
| --- | --- |
| **Supply & demand** | Production levels, agricultural yields, inventories, global consumption trends and economic conditions. |
| **Weather** | Droughts, frosts and excessive rainfall can devastate crops and create supply shocks. |
| **Geopolitics** | Political stability, trade policies and tariffs in major producing countries. |
| **Macroeconomics** | Interest rates, inflation and currency exchange rates. |

## Knowledge Check — Price Drivers

**Prompt:** How do supply and demand dynamics affect prices? What weather patterns influence production? How can geopolitical factors impact futures contracts?

**My answer:**

1. **Supply & demand.** Supply and demand are the primary drivers of commodity prices. When production falls — due to poor yields or low inventory — the supply curve shifts and prices rise. Global consumption trends and economic conditions drive demand; a surge in coffee consumption raises the equilibrium futures price.
2. **Weather patterns.** Agricultural commodities are highly sensitive to the environment. Prolonged droughts, unseasonal frosts (common in Brazil) and excessive rainfall can devastate crops, creating supply shocks and sudden price spikes.
3. **Geopolitical factors.** Political instability, trade policies and tariffs in major producers (e.g., Vietnam or Colombia) can restrict supply, introduce political risk into futures contracts and shift the futures curve — for example into **backwardation** during a crisis.

## Factors That Impact Coffee Futures

### Supply shocks
- **Natural disasters:** droughts or frosts in Brazil or Colombia reduce yields and drive prices up.
- **Pests and diseases:** the coffee borer beetle or coffee leaf rust can devastate crops.
- **Unexpected weather:** unseasonal rains affect both the quality and quantity of coffee.

### Demand shifts
- **Economic conditions:** growth raises disposable income and coffee consumption; recessions do the opposite.
- **Consumer preferences:** specialty coffee and emerging-market consumption boost demand.
- **Health trends:** a shift toward perceived healthier beverages can reduce demand.

### Geopolitical events
- **Political instability:** unrest or conflict disrupts production and exports.
- **Trade policies:** tariffs or export bans restrict flows and push prices up.
- **Currency fluctuations:** a stronger local currency makes exports more expensive and can reduce demand.

## Quantitative Techniques

| Technique | Purpose |
| --- | --- |
| **Linear regression** | Predict relationships between a dependent variable and one or more independent variables; market trend analysis. |
| **Black-Scholes** | Option pricing using volatility, strike price and time to maturity. |
| **Monte Carlo simulation** | Estimate the range and likelihood of different price scenarios for derivative pricing and risk management. |

## Applying the Models

### 1. Cost of Carry Model

The futures price equals the spot price plus the cost of carrying the asset to maturity:

$$F_t = S_t \cdot e^{(r+d)T}$$

**Given data**

| Input | Value |
| --- | --- |
| Spot price $S_t$ | \$1.20 / lb |
| Risk-free rate $r$ | 2% p.a. |
| Storage cost $d$ | 1% p.a. |
| Time to maturity $T$ | 0.5 years |

**Calculation**

$$F_t = 1.20 \cdot e^{(0.02 + 0.01) \cdot 0.5} = 1.20 \cdot e^{0.015} \approx 1.20 \cdot 1.0151 = 1.2181$$

**Result:** the fair price of the coffee futures contract is approximately **\$1.218 per pound**.

**Python implementation**

```python
import numpy as np

# Given values
S_t = 1.20   # Spot price ($/lb)
r = 0.02     # Risk-free rate (2% p.a.)
d = 0.01     # Storage cost (1% p.a.)
T = 0.5      # Time to maturity (years)

# Futures price
F_t = S_t * np.exp((r + d) * T)
print(f"The fair price of the coffee futures contract is ${F_t:.3f} per pound.")
```

```text
The fair price of the coffee futures contract is $1.218 per pound.
```

### 2. Black-Scholes Model

For a European call option:

$$C = S_0 N(d_1) - X e^{-rT} N(d_2)$$

$$d_1 = \frac{\ln(S_0/X) + \left(r + \tfrac{1}{2}\sigma^2\right)T}{\sigma\sqrt{T}}, \qquad d_2 = d_1 - \sigma\sqrt{T}$$

> **Note:** for commodities it is common to use the **Black-76** variant, which takes the futures price as the underlying instead of the spot price, because spot prices for physical goods are harder to track due to logistics and quality variation.

**Given data**

| Input | Value |
| --- | --- |
| Spot price $S_0$ | \$1.20 / lb |
| Strike price $X$ | \$1.25 / lb |
| Risk-free rate $r$ | 2% p.a. |
| Time to maturity $T$ | 0.5 years |
| Volatility $\sigma$ | 25% |

**Python implementation**

```python
import numpy as np
from scipy.stats import norm

# Given values
S_0 = 1.20    # Spot price ($/lb)
X = 1.25      # Strike price ($/lb)
r = 0.02      # Risk-free rate (2% p.a.)
T = 0.5       # Time to maturity (years)
sigma = 0.25  # Volatility (25%)

# d1 and d2
d1 = (np.log(S_0 / X) + (r + 0.5 * sigma**2) * T) / (sigma * np.sqrt(T))
d2 = d1 - sigma * np.sqrt(T)

# Call option price (Black-Scholes)
C = S_0 * norm.cdf(d1) - X * np.exp(-r * T) * norm.cdf(d2)
print(f"The price of the call option is ${C:.3f}.")
```

```text
d1 = -0.0860
d2 = -0.2627
The price of the call option is $0.068.
```

### 3. Monte Carlo Simulation

Coffee prices are driven by chaos — weather in Brazil, port strikes, supply shocks — that a single formula cannot capture. Monte Carlo simulates thousands of possible futures using **geometric Brownian motion (GBM)**:

$$S_{t+\Delta t} = S_t \cdot \exp\left(\left(r - \tfrac{1}{2}\sigma^2\right)\Delta t + \sigma\sqrt{\Delta t}\, Z\right), \qquad Z \sim \mathcal{N}(0,1)$$

**Python implementation**

```python
import numpy as np

# Simulation parameters
S_0 = 1.20            # Spot price ($/lb)
r = 0.02              # Risk-free rate (2% p.a.)
sigma = 0.25          # Volatility (25%)
T = 0.5               # Time to maturity (years)
num_simulations = 10_000
num_steps = 252       # Trading days

dt = T / num_steps

np.random.seed(42)    # Reproducibility
price_paths = np.zeros((num_steps, num_simulations))
price_paths[0] = S_0

for t in range(1, num_steps):
    z = np.random.standard_normal(num_simulations)
    price_paths[t] = price_paths[t - 1] * np.exp(
        (r - 0.5 * sigma**2) * dt + sigma * np.sqrt(dt) * z
    )

# Average simulated price at maturity
average_simulated_price = np.mean(price_paths[-1])
print(f"The average simulated price of the coffee futures contract at maturity is ${average_simulated_price:.3f}.")
```

```text
The average simulated price of the coffee futures contract at maturity is $1.209.
```

> With 10,000 paths and 252 daily steps, the simulated average converges close to the theoretical expectation $E[S_T] = S_0 e^{rT} = 1.20 \cdot e^{0.01} \approx \$1.212$.

## Data Sources & Tools

| Data | Source |
| --- | --- |
| Spot prices | Bloomberg, Reuters, International Coffee Organization (ICO) |
| Risk-free rates | US Department of the Treasury, FRED |
| Storage costs | Commodity market reports, industry publications |
| Volatility | Yahoo Finance, historical price databases |

| Tool | Use |
| --- | --- |
| **Python** | Data analysis and simulations — NumPy, SciPy, pandas |
| **Spreadsheet** | Initial data gathering and simple calculations |

## Knowledge Check — Model Concepts

**Prompt:** What is the cost of carry formula and what does each component represent? How does Black-Scholes apply to commodities? What is the purpose of Monte Carlo simulations?

**My answer:**

1. **Cost of carry.** The futures price is the current spot price plus the extra cost of holding the asset until expiry. We take the interest rate $r$ (cost of the money tied up) and add storage costs $d$ (warehousing, insurance). In coffee we also consider the **convenience yield** — a bonus for having physical beans on hand. In a shortage, holding the actual beans is worth more than holding paper, which lowers the futures price relative to spot.
2. **Black-Scholes for commodities.** The original model was built for stocks; for commodities we use **Black-76**, which uses the futures price $F$ as the underlying instead of the spot price. Futures prices already bake in storage and interest costs, making them a more reliable baseline.
3. **Monte Carlo.** A single formula cannot predict chaos, so we simulate thousands of random "what-if" scenarios using GBM and historical volatility. The result is a **distribution** of possible future paths; averaging them gives a realistic fair value that a single calculation cannot provide.

## Worked Analysis

**Given:** spot \$1.20/lb · risk-free 2% · storage 1% · $T$ = 0.5y · strike \$1.25 · volatility 25%.

| Model | Result |
| --- | --- |
| Cost of carry (futures price) | **\$1.218 / lb** |
| Black-Scholes (call option) | **\$0.068** |
| Monte Carlo (average at maturity) | **\$1.209** |

**Interpretation:** the futures contract trades slightly above spot, reflecting the positive cost of carry (interest + storage). The call option is out of the money (strike \$1.25 > spot \$1.20), so its premium is small. The Monte Carlo average sits close to the theoretical forward price, confirming the simulation is well calibrated.

## Example Answer

**Pricing a futures contract:** cost of carry model — $F_t = S_t e^{(r+d)T}$ — ensuring the futures price reflects the cost of holding the commodity over time.

**Structuring securities:** linear regression to quantify relationships between coffee prices and economic factors, plus geometric Brownian motion to simulate future price paths and design payouts.

**Managing risk:** VaR (maximum expected loss at a confidence level), Monte Carlo (distribution of future prices) and GARCH (volatility forecasting).

## Key Takeaways

- Commodity prices are driven by a mix of physical factors (weather, supply shocks) and financial factors (rates, FX, geopolitics).
- The cost of carry model connects spot and futures prices; convenience yield explains deviations such as backwardation.
- Black-76 is the commodity-friendly variant of Black-Scholes because it prices off the futures curve.
- Monte Carlo turns uncertainty into a distribution, which is far more useful for risk management than a single point estimate.

---

[← Previous: Task 1](task-1-financial-math.md) · [Back to README](../README.md) · [Next: Task 3 →](task-3-hedging-securities.md)
