# Trade, Policy, and Carbon: Assessing Globalization in Climate Agreements

## Project Overview
This repository evaluates whether strict domestic climate regulations paradoxically expand a nation's transnational carbon footprint by outsourcing carbon-heavy production chains to foreign trading partners (carbon leakage).The analysis processes a 12-year panel dataset (2010–2022) tracking four major European economies: France, Germany, the Netherlands, and the United Kingdom. Rather than relying on a simple pooled regression, this project implements Two-Way Fixed Effects (TWFE) and rigorous robustness checks to isolate structural distortions and identify the true economic drivers of the transnational emissions gap.

---

## Repository Structure
The project is modularized into three sequential Jupyter Notebooks to maintain clear separation of concerns between data exploration, causal inference, and model stability testing:

### 01_eda.ipynb: Data Ingestion, Cleaning & Exploratory Analysis ###
* Aligns global trade datasets with territorial and consumption carbon metrics.
* Exposes the "Rotterdam Effect" structural outlier and identifies variables with critical multicollinearity.

### 02_modelling.ipynb: Econometric Estimation & Fixed-Effects ###
* Implements Two-Way Fixed Effects to control for unobserved country and year characteristics.
* Evaluates the direct impacts of environmental policy stringency and European carbon market pricing.

### 03_robustness_checks.ipynb: Stress-Testing & Sensitivity Matrix ###
* Validates the core findings against temporal shocks, reverse-causality lags, and extreme sample exclusions.

---

## Key Empirical Findings
1. The Aggregate Trade Null Effect
Across all baseline and interaction model layers, aggregate trade openness (trade_percent_gdp) shares no statistically significant relationship with the emissions gap. Broad globalization metrics do not serve as reliable leading indicators or drivers of cross-border carbon leakage.
2. Environmental Policy Regulates the Gap
Controlling for country-specific baseline traits reveals that a 1-point increase on the OECD Environmental Policy Stringency (EPS) Index is associated with a contraction of the emissions gap by ~23.77 million tonnes ($p = 0.021$). Stricter domestic climate regulations compress the outsourced carbon footprint rather than expanding it.
3. Carbon Pricing Drives the Leakage Incentive
Model estimations reveal that the financial cost of emissions—tracked via the European Union Allowance price (eua_price)—acts as a significant driver of carbon outsourcing. For every €1 increase in the local carbon permit price, the consumption emissions gap expands by approximately 220,000 tonnes ($p < 0.001$), illustrating a tangible market-cost pass-through incentive.

---

## Econometric Rigour & Robustness Checks
To guarantee absolute statistical defensibility for interview and portfolio reviews, the findings were subjected to three explicit stress tests in Notebook 3:
* Pandemic Volatility Test: Excluding the 2020–2022 COVID-19 shock leaves the baseline trade coefficient statistically unchanged ($p = 0.831$), proving the null effect is a long-term structural reality.
* Causality Lag Probe: Running regressions against lagged trade vectors ($t-1$) confirms that historical economic trade intensity does not predict future carbon leakage variations ($p = 0.249$).
* Transit Outlier Exclusion: Removing the Netherlands (the primary regional shipping and re-export transit hub) reveals a significant negative relationship (-4.07, ($p = 0.026$)) for the remaining consumer markets (UK, France, Germany), demonstrating that trade openness can correlate with cleaner domestic consumption profiles.

---

## Strategic Policy Recommendation
The absence of a broad trade-leakage effect implies that aggregate trade barriers are inefficient climate mitigation tools. Instead, climate governance frameworks should prioritize target-specific financial market instruments, such as the Carbon Border Adjustment Mechanism (CBAM), to directly address the carbon-pricing cost differentials that influence supply-chain routing.
