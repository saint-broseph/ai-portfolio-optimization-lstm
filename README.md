# 📈 An Empirical Comparison of LSTM-Based Portfolio Rebalancing and Mean–Variance Optimization

**Adaptive Portfolio Optimization: Learning-Based Rebalancing vs. Markowitz MVO**

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Institution: BITS Pilani](https://img.shields.io/badge/Institution-BITS%20Pilani-red.svg)](https://www.bits-pilani.ac.in/goa/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## 📌 Executive Summary

This repository presents an empirical comparison between a learning-based portfolio rebalancing strategy and the classical Markowitz Mean–Variance Optimization (MVO) framework. Using a five-year dataset (2019–2024) spanning cryptocurrencies, equities, and commodities (**BTC, ETH, NVDA, SPY, GLD**), we evaluate how adaptive rebalancing compares to static optimization under realistic trading constraints.

The learning-based strategy uses a Long Short-Term Memory (LSTM) network trained with a drawdown-sensitive loss function to dynamically update portfolio weights.

**Key Finding:**  
The LSTM-based strategy achieved a higher cumulative return of **166.42%**, outperforming the MVO baseline by **15.46%**. However, this improvement came with higher drawdowns, while MVO remained superior in risk-adjusted efficiency (Sortino Ratio **4.24 vs 3.30**).

These results highlight a fundamental trade-off between adaptive growth and risk-efficient capital preservation.

---

## 📈 Performance Visualization
![Final Performance Comparison](images/final_comparison.png)

## 📉 Underwater Drawdown Plot
![Underwater Drawdown Plot](images/underwater_plot.png)

---

## 📊 Performance Comparison

### 1. Overall Results (Full Test Period)
| Metric | LSTM Strategy | MVO Strategy | Difference |
|------|---------------|--------------|------------|
| **Final Portfolio Return** | **166.42%** | 150.96% | **+15.46%** |
| **Maximum Drawdown** | -25.98% | **-17.68%** | -8.30% |
| **Sortino Ratio** | 3.30 | **4.24** | -0.94 |
| **Post-Fee Return** | **166.15%** | 150.72% | **+15.43%** |

---

### 2. Bear Market Robustness (2022)
| Metric | LSTM Strategy | MVO Strategy | Difference |
|------|---------------|--------------|------------|
| **Total Return** | **121.47%** | 110.91% | **+10.56%** |
| **Maximum Drawdown** | -19.81% | **-10.41%** | -9.40% |

---

## 🛠️ Technical Implementation

### Drawdown-Sensitive Loss Function
Instead of minimizing prediction error, the model directly optimizes portfolio performance:

**Loss Function**

Loss = −E(Rₚ) + λ · max(0, −Rₚ)²

The penalty parameter λ ∈ [10, 50] controls the trade-off between return maximization and drawdown sensitivity.


---

### Training Stability
Training instability caused by high crypto volatility was addressed using:
- **Gradient Clipping** (max norm = 1.0)
- **Reduced Learning Rate** (0.0005)

These adjustments ensured stable convergence across all experiments.

---

### Real-World Constraints
- **Transaction Costs:** 0.1% per rebalance
- **Position Limits:** Max 40% per asset
- **No leverage or short selling**

---

## 🧪 Key Observations

- **Adaptive Behavior:** The LSTM strategy adjusted allocations during high-momentum periods where the static MVO portfolio remained unchanged.
- **Allocation Concentration:** The learning-based strategy aggressively concentrated into dominant assets (e.g., BTC), while MVO maintained defensive diversification (e.g., GLD).
- **Temporal Robustness:** The LSTM strategy generated positive excess returns in 2 out of 3 rolling evaluation windows.

---

## 👨‍🔬 Author

**Tanishq Sahu**  
BITS Pilani, K.K. Birla Goa Campus  
Goa, India  

📧 [sahutanishq06@gmail.com](mailto:sahutanishq06@gmail.com)  
🔗 [LinkedIn](https://www.linkedin.com/in/tanishq-sahu-655786230/)

