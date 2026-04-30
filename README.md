# Security-Constrained Economic Dispatch Optimization
### *Optimizing Operational Costs for a Micro-grid*

## **Project Overview**
This project develops a **stochastic linear programming (LP)** model to minimize the daily operational expenditure (OPEX) of an institutional micro-grid. By integrating a **Battery Energy Storage System (BESS)** and accounting for **Time-of-Day (ToD) pricing**, the algorithm mathematically decides the most cost-effective power dispatch schedule across a 24-hour horizon.

## **Key Technical Advancements**
*   **Stochastic Load Balancing:** Unlike deterministic models, this simulation introduces a random noise multiplier, $\epsilon_{t} \sim \mathcal{U}(1.0, 1.20)$, simulating unpredictable 20% demand spikes to stress-test grid resilience.
*   **Multi-Variable Optimization:** The model manages **144 interconnected decision variables** (6 variables per hour over 24 hours) to maintain supply-demand equilibrium.
*   **Battery Physics Modeling:** Includes State of Charge (SoC) constraints and round-trip efficiency ($\eta = 0.95$) to prevent hardware degradation while maximizing off-peak charging.

---

## **The Mathematical Model**

### **Objective Function**
The goal is to minimize the total daily cost ($Z$) across all energy sources and battery wear:
$$Z = \sum_{t=1}^{24} (C_{s}s_{t} + C_{w}w_{t} + C_{g,t}g_{t} + C_{b}(b_{t}^{in} + b_{t}^{out}))$$

### **Primary Constraints**
1.  **Supply-Demand Equilibrium (Stochastic):** $s_{t} + w_{t} + g_{t} + b_{t}^{out} - b_{t}^{in} = L_{t} \cdot \epsilon_{t}$
2.  **Battery Energy Balance:** $E_{t} = E_{t-1} + (\eta \cdot b_{t}^{in}) - (\frac{b_{t}^{out}}{\eta})$
3.  **Capacity Limits:** $E_{t} \le 250 \text{ kWh}$ and non-negativity for all sources

---

## **Financial Impact & Results**
The model was tested against a "Chaotic Day" scenario with fluctuating grid prices (ranging from Rs. 4.0 to Rs. 15.0 per kWh)[cite: 1].

| Metric | Result (INR) |
| :--- | :--- |
| **Baseline Daily Cost** (Standard Grid) | **Rs. 15,009.47** |
| **Optimized Daily Cost** (LP Model) | **Rs. 13,234.79** |
| **Projected Annual Savings** | **~Rs. 6,55,697.31** |

**Key Finding:** The battery acts as a financial insurance policy; during "worst-case" demand surges, the algorithm's ability to avoid peak grid rates increased comparative savings significantly.

---

## **Tools & Technologies**
*   **Language:** R
*   **Solver:** `lpSolve` 
*   **Documentation:** LaTeX (Technical Report)

