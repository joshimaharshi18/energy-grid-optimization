# energy-grid-optimization
# Optimization of Energy Grid Operational Costs
**Status:** Ongoing Collaborative Research

## Project Overview
This project focuses on minimizing the daily Operational Expenditure of an energy grid through mathematical modeling and Linear Programming (LP). We are currently formulating constraints for supply-demand equilibrium and system losses to optimize load distribution using R.

## Research Objectives
* Minimize the total objective function for grid costs:
  
  $$ \text{Minimize} \quad Z = \sum_{t=1}^{24} \left( C_{\text{solar}} \cdot s_t + C_{\text{wind}} \cdot w_t + C_{\text{grid},t} \cdot g_t + C_{\text{batt}} \cdot (b_t^{in} + b_t^{out}) \right) $$
  
* Model supply-demand constraints to ensure grid stability.
* Evaluate cost-reduction scenarios using numerical methods.

## Tools & Technologies
* **R**
* **Methodology:** Linear Programming, Numerical Analysis

## How to Run
*Note: The core simulation scripts are currently being refined in a private local branch. Documentation and mathematical formulations will be updated periodically.*

The synthetic 24-hour time-series data used for this simulation—including Time-of-Use grid charges is uploaded
