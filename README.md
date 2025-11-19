# bloomberg-workshop-shpe-2025

# AI-Driven Bond Pricing (2025 SHPE Convention Workshop by Bloomberg)

## Basic Pipeline for an AI Bond-Pricing System
### Step 1. Data Collection
Trades, quotes, bond attributes, etc.
Filter outliers and apply time decay weighting: prioritize recent, high quality data
### Step 2. Direct Pricing
If sufficient direct market data (trades, quotes) exists for the target bond: 
- Estimate bid/ask prcies from direct market data
### Step 3. Cohort Pricing 
Cohort selection: comparable bonds using similarity measure based on issuer, sector, coupon, maturity, rating, liquidity, etc. For each selected bond: 
- If sufficient direct market data, estimate bid/ask prices. 
- Normalize cohort prices.
### Step 4. Structural Features
Track issuer, sector and credit yield curves. Periodically update cohort clusters and similarity measures satisfying financial structured and consistency.
### Step 5. Final Price
Combines results from:
- Direct bond pricing (Step 2) if available
- Dohort-based estimates (Step 3)
- Structure similarity and tracked curves (Step 4)


Assign higher weights to direct market observations when available


## Model Types
* Traditional heuristics that iterate through steps like:
    * Outlier detection; may include a human in the loop (HITL) process
    * Regime shift detection
    * Bid-ask spread estimation
    * [Auto] regression models
    * Constrained optimization algos (satisfy expected market behaviors)
* Matrix factorization models
* Tree-based regression models
* [Temporal] neural networks: LSTMs, CNNs,..
* Deep neural models: attention layer encoders, transformers, diffusers, ...

**Trade-offs:** accuracy, explanations, cost and effective use of human experts (HITL)

## Glossary
### Bond characteristics
- **Principal:** initial amount of money borrowed by the bond issuer, repaid to the bondholder at maturity
- **Coupon:** periodic interest payment made by the bond issuer to the bond holder,
- **Maturity:** date in the future when the borrower will pay back the Principal.
### Market conditions impacting pricing
- **Interest rates:** measure of the "time value of money". When market interest rates rise, the value of existing bonds with lower coupons typically falls and vice versa
- **Default probability:** likelihood bond issuer will fail to make its promised interest or principal payments. A higher default probability generally leads to a lower bond price.
- **Discount factor:** factor used to calculate present value of future cash flows. It accounts for the time value of money and the risk associated with the cash flow (mostly default risk).


Workshop Exercise: Your client wants to trade 3 bonds, associated with a school district. Estimate prices!
| Bond ID | Coupon | Maturity| BUY Price (per $100) | SELL Price (per $100) | B/S Spread (SELL - BUY)
|---|---|---|---|---|---|
| A | 5% | 2035-08-01 |
| B | 5% | 2049-08-01  |
| C | 5.25% | 2049-08-01  |