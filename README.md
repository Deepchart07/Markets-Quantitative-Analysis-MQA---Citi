# ☕ Citi Markets Quantitative Analysis (MQA) — Job Simulation

> A documented walkthrough of my learning journey through Citi's Markets Quantitative Analysis job simulation.

## Overview

This repository documents the four tasks I completed in the **Citi Markets Quantitative Analysis (MQA) Job Simulation**, a program designed to mirror the day-to-day work of a quantitative analyst intern in Citi's Markets division.

Across the simulation I worked on a single, realistic project: **designing a futures contract for the coffee commodity** and building the quantitative framework around it — from pricing and hedging to risk management.

## The Project

Citi's Markets Quant team is collaborating with coffee producers and traders who need a streamlined, standardized way to hedge against price volatility. The project has two goals:

- Design a coffee futures contract that accurately reflects market dynamics and supports price discovery.
- Build a comprehensive risk management strategy around the contract, protecting both clients and the firm.

## Team

| Member | Role |
| --- | --- |
| **Edward Rosales** (me) | Quantitative Analyst Intern |
| Aisha | Senior Quantitative Analyst — Manager |
| Raj | Quantitative Analyst — Colleague |
| Rae | Quantitative Analyst — Colleague (forecasting & Python) |
| Sarah | Quantitative Analyst — Colleague (risk management) |

## Tasks

| # | Task | Key topics | Document |
| --- | --- | --- | --- |
| 1 | Financial Math Fundamentals & Team Structure | Asset classes, probability & statistics, calculus, modeling | [Task 1](docs/task-1-financial-math.md) |
| 2 | Pricing Commodities — Coffee | Futures pricing, cost of carry, Black-Scholes, Monte Carlo | [Task 2](docs/task-2-coffee-futures.md) |
| 3 | Hedging & Structuring Securities | Options, swaps, structured notes, digital options | [Task 3](docs/task-3-hedging-securities.md) |
| 4 | Managing Risk Across Market Trade Units | VaR, stress testing, credit & operational risk | [Task 4](docs/task-4-risk-management.md) |

## Key Learnings

### 1. Financial math is the language of markets
Probability, calculus and stochastic processes are not academic exercises — they are the tools used to price derivatives, model uncertainty and quantify risk. The Black-Scholes PDE and geometric Brownian motion showed me how continuous mathematics translates directly into market prices.

### 2. Pricing is more than plugging numbers into a formula
The cost of carry model is simple, but real markets add **convenience yield**, supply shocks and **backwardation**. Pricing a commodity means understanding the physical market behind the contract, not just the equation.

### 3. Hedging and structuring are two sides of the same coin
Options, swaps and structured notes let us reshape a client's risk profile. The right product depends on the client's risk tolerance — from commodity-linked bonds for conservative investors to digital options for high-risk profiles.

### 4. Risk management is a continuous process
VaR, stress testing and Expected Shortfall measure risk, but the real discipline is **monitoring and adjusting**. Market, credit and operational risks require different tools and a constant feedback loop.

## Skills Demonstrated

- **Quantitative modeling:** cost of carry, Black-Scholes, Monte Carlo with geometric Brownian motion
- **Risk analytics:** VaR, CVaR / Expected Shortfall, stress testing, GARCH
- **Derivatives & structuring:** futures, options, swaps, structured notes, digital options
- **Python:** NumPy, SciPy, simulation workflows
- **Communication:** translating quantitative models into client-ready proposals

## Repository Structure

```
.
├── README.md
└── docs/
    ├── task-1-financial-math.md
    ├── task-2-coffee-futures.md
    ├── task-3-hedging-securities.md
    └── task-4-risk-management.md
```

## Disclaimer

This repository is for educational and portfolio purposes only. It documents a **simulated** job experience and does not contain confidential Citi information.
