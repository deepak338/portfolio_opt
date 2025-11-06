# 📊 Portfolio Optimization Project

**An end-to-end financial portfolio optimization system using Modern Portfolio Theory and Python**

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Active-success)

---

## 🎯 Project Overview

This project implements **Modern Portfolio Theory (MPT)** to construct optimal investment portfolios that maximize returns while minimizing risk. Using historical stock price data, the system calculates efficient frontiers, optimal asset allocations, and provides actionable investment insights.

### **Key Objectives**
- Analyze historical stock performance and calculate risk-return metrics
- Construct efficient frontier portfolios using mean-variance optimization
- Identify optimal portfolio weights for maximum Sharpe ratio
- Visualize portfolio performance and risk characteristics
- Provide data-driven investment recommendations

---

## ✨ Features

- **Data Collection**: Automated stock price data retrieval from Yahoo Finance API
- **Statistical Analysis**: Calculate returns, volatility, correlation matrices, and covariance
- **Portfolio Optimization**: 
  - Minimum variance portfolio
  - Maximum Sharpe ratio portfolio
  - Efficient frontier generation
  - Monte Carlo simulation for portfolio scenarios
- **Risk Metrics**: Value at Risk (VaR), Sharpe ratio, Sortino ratio, maximum drawdown
- **Interactive Visualizations**: 
  - Efficient frontier plots
  - Correlation heatmaps
  - Asset allocation pie charts
  - Historical performance comparison
- **Backtesting**: Test portfolio strategies against historical data

---

## 🛠️ Technologies Used

| Category | Tools |
|----------|-------|
| **Language** | Python 3.8+ |
| **Data Analysis** | pandas, NumPy |
| **Optimization** | SciPy, CVXPY |
| **Visualization** | Matplotlib, Seaborn, Plotly |
| **Data Source** | yfinance (Yahoo Finance API) |
| **Statistics** | statsmodels |
| **Notebooks** | Jupyter Notebook |

---

## 📦 Installation & Setup

### **Prerequisites**
- Python 3.8 or higher
- pip package manager

### **Step 1: Clone the Repository**
```bash
git clone https://github.com/deepak338/portfolio_opt.git
cd portfolio_opt
```

### **Step 2: Create Virtual Environment (Optional but Recommended)**
```bash
# On Windows
python -m venv venv
venv\Scripts\activate

# On macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

### **Step 3: Install Required Packages**
```bash
pip install -r requirements.txt
```

**Or install manually:**
```bash
pip install pandas numpy scipy matplotlib seaborn yfinance cvxpy plotly jupyter
```

### **Step 4: Verify Installation**
```bash
python -c "import pandas, numpy, scipy, matplotlib; print('All packages installed successfully!')"
```

---

## 🚀 Getting Started

### **Quick Start Example**

Here's how to run a basic portfolio optimization:

```python
# Import required libraries
import pandas as pd
import numpy as np
from portfolio_optimizer import PortfolioOptimizer

# Define stock tickers and date range
tickers = ['AAPL', 'MSFT', 'GOOGL', 'AMZN', 'TSLA']
start_date = '2020-01-01'
end_date = '2024-01-01'

# Initialize optimizer
optimizer = PortfolioOptimizer(tickers, start_date, end_date)

# Get optimal portfolio
optimal_weights = optimizer.maximize_sharpe_ratio()
print("Optimal Portfolio Weights:")
print(optimal_weights)

# Visualize efficient frontier
optimizer.plot_efficient_frontier()
```

### **Running the Jupyter Notebook**

For detailed analysis with visualizations:

```bash
jupyter notebook portfolio_optimization_analysis.ipynb
```

---

## 📂 Project Structure

```
portfolio_opt/
│
├── data/                          # Raw and processed data
│   ├── raw/                       # Downloaded stock prices
│   └── processed/                 # Cleaned datasets
│
├── notebooks/                     # Jupyter notebooks
│   └── portfolio_optimization_analysis.ipynb
│
├── src/                           # Source code
│   ├── data_loader.py            # Data collection functions
│   ├── portfolio_optimizer.py    # Optimization algorithms
│   ├── risk_metrics.py           # Risk calculation functions
│   └── visualizations.py         # Plotting functions
│
├── results/                       # Output files
│   ├── figures/                  # Generated plots
│   └── reports/                  # Analysis reports
│
├── requirements.txt               # Python dependencies
├── README.md                      # This file
└── LICENSE                        # MIT License
```

---

## 📊 Methodology & Theory

### **Modern Portfolio Theory (MPT)**

This project is based on **Harry Markowitz's Modern Portfolio Theory**, which states that investors can construct portfolios to maximize expected return based on a given level of market risk.

#### **Key Concepts:**

1. **Expected Return (μ)**
   ```
   E(Rp) = Σ wi * E(Ri)
   ```
   Where wi is weight of asset i, E(Ri) is expected return

2. **Portfolio Variance (σ²)**
   ```
   σp² = wᵀ Σ w
   ```
   Where Σ is the covariance matrix

3. **Sharpe Ratio**
   ```
   Sharpe Ratio = (Rp - Rf) / σp
   ```
   Measures risk-adjusted return (Rf is risk-free rate)

4. **Efficient Frontier**
   - Set of optimal portfolios offering highest expected return for a defined level of risk
   - Portfolios below the frontier are sub-optimal

### **Optimization Approach**

The project uses **Quadratic Programming** to solve:

```
Maximize: Sharpe Ratio
Subject to:
  - Σ wi = 1 (weights sum to 1)
  - 0 ≤ wi ≤ 1 (long-only constraint)
  - Portfolio constraints (optional)
```

---

## 📈 Key Visualizations

### **1. Efficient Frontier**
Shows the risk-return tradeoff across all possible portfolios.

```python
optimizer.plot_efficient_frontier(show_cml=True)
```

**What it shows:**
- Blue curve: Efficient frontier (optimal portfolios)
- Red star: Maximum Sharpe ratio portfolio
- Green star: Minimum variance portfolio
- Individual assets plotted as scatter points

---

### **2. Correlation Heatmap**
Visualizes how assets move together.

```python
optimizer.plot_correlation_matrix()
```

**Interpretation:**
- Values close to +1: Assets move together (high correlation)
- Values close to -1: Assets move opposite (negative correlation)
- Values near 0: No clear relationship
- Diversification benefit comes from low/negative correlations

---

### **3. Optimal Asset Allocation**
Pie chart showing recommended portfolio weights.

```python
optimizer.plot_allocation(optimal_weights)
```

**Use Case:**
- If you have $10,000 to invest, this shows how to split it
- Example: 30% AAPL, 25% MSFT, 20% GOOGL, etc.

---

### **4. Historical Performance Comparison**
Compares optimized portfolio vs equal-weight portfolio vs individual assets.

```python
optimizer.plot_cumulative_returns()
```

**Insights:**
- Shows if optimization strategy beats simple equal allocation
- Visualizes compound growth over time
- Identifies periods of outperformance/underperformance

---

### **5. Risk-Return Scatter**
Individual asset risk vs return positioning.

```python
optimizer.plot_risk_return_scatter()
```

**Key Takeaways:**
- Top-right: High risk, high return assets
- Bottom-left: Low risk, low return assets
- Optimal portfolio usually sits on efficient frontier line

---

## 🎓 Example Workflow

### **Complete Analysis Pipeline:**

```python
# 1. Import and initialize
from portfolio_optimizer import PortfolioOptimizer

tickers = ['AAPL', 'MSFT', 'JPM', 'JNJ', 'PG']  # Mix of tech, finance, healthcare, consumer
optimizer = PortfolioOptimizer(tickers, '2019-01-01', '2024-01-01')

# 2. Load and explore data
data = optimizer.get_price_data()
print("Data shape:", data.shape)
print("Missing values:", data.isnull().sum())

# 3. Calculate statistics
returns = optimizer.calculate_returns()
print("\nAnnualized Returns:")
print(returns.mean() * 252)  # 252 trading days

print("\nAnnualized Volatility:")
print(returns.std() * np.sqrt(252))

# 4. Generate portfolios
results = optimizer.generate_random_portfolios(num_portfolios=10000)

# 5. Find optimal allocations
max_sharpe_weights = optimizer.maximize_sharpe_ratio()
min_vol_weights = optimizer.minimize_volatility()

print("\n=== OPTIMAL PORTFOLIO (Max Sharpe) ===")
for ticker, weight in max_sharpe_weights.items():
    print(f"{ticker}: {weight*100:.2f}%")

# 6. Calculate performance metrics
expected_return, volatility, sharpe = optimizer.portfolio_performance(max_sharpe_weights)
print(f"\nExpected Annual Return: {expected_return*100:.2f}%")
print(f"Annual Volatility: {volatility*100:.2f}%")
print(f"Sharpe Ratio: {sharpe:.3f}")

# 7. Generate visualizations
optimizer.plot_efficient_frontier()
optimizer.plot_correlation_matrix()
optimizer.plot_allocation(max_sharpe_weights, title="Optimal Portfolio Allocation")

# 8. Backtest strategy
backtest_results = optimizer.backtest_portfolio(max_sharpe_weights)
print("\n=== BACKTEST RESULTS ===")
print(f"Total Return: {backtest_results['total_return']*100:.2f}%")
print(f"Max Drawdown: {backtest_results['max_drawdown']*100:.2f}%")
print(f"Winning Months: {backtest_results['win_rate']*100:.1f}%")
```

---

## 📊 Sample Results

### **Example Output: Tech-Heavy Portfolio**

**Input Stocks:** AAPL, MSFT, GOOGL, NVDA, META

**Optimal Allocation (Max Sharpe Ratio):**
```
AAPL:  28.5%
MSFT:  32.1%
GOOGL: 15.3%
NVDA:  18.7%
META:   5.4%
```

**Performance Metrics:**
- Expected Annual Return: 22.4%
- Annual Volatility: 28.1%
- Sharpe Ratio: 0.73
- Maximum Drawdown: -31.2%

**Compared to Equal-Weight Portfolio:**
- Optimized portfolio outperformed by 3.8% annually
- Reduced volatility by 4.2%
- Better risk-adjusted returns (higher Sharpe ratio)

---

## 🎯 Business Value & Applications

### **For Individual Investors:**
- Construct diversified portfolios aligned with risk tolerance
- Make data-driven investment decisions
- Understand portfolio risk characteristics
- Rebalance efficiently

### **For Portfolio Managers:**
- Optimize large-scale portfolios systematically
- Conduct scenario analysis and stress testing
- Generate client reports with clear visualizations
- Implement quantitative investment strategies

### **For Data Science Portfolios:**
- Demonstrates end-to-end data science workflow
- Shows financial domain knowledge
- Highlights optimization and statistical skills
- Real-world application with measurable outcomes

---

## 💡 Key Insights & Learnings

### **What I Discovered:**

1. **Diversification Matters**: 
   - A well-diversified portfolio with 5-10 uncorrelated assets significantly reduces risk without sacrificing returns

2. **Correlation is Key**: 
   - Including assets with negative or low correlation improves the efficient frontier
   - Tech stocks tend to move together (high correlation)

3. **Sharpe Ratio Limitations**:
   - Assumes normal distribution of returns (not always true in real markets)
   - Doesn't account for tail risks (black swan events)

4. **Backtesting Reality Check**:
   - Optimized portfolios based on historical data may not perform as well in future markets
   - Transaction costs and taxes can erode theoretical gains

5. **Practical Application**:
   - Most benefit comes from initial diversification
   - Over-optimization can lead to overfitting
   - Regular rebalancing (quarterly/annually) is crucial



---

## 📚 References & Resources

### **Academic Papers:**
- Markowitz, H. (1952). "Portfolio Selection". The Journal of Finance
- Sharpe, W.F. (1964). "Capital Asset Prices: A Theory of Market Equilibrium"

### **Books:**
- "Quantitative Risk Management" - Alexander McNeil
- "Python for Finance" - Yves Hilpisch
- "Advances in Financial Machine Learning" - Marcos López de Prado

### **Online Resources:**
- [Modern Portfolio Theory - Investopedia](https://www.investopedia.com/terms/m/modernportfoliotheory.asp)
- [Portfolio Optimization - QuantConnect](https://www.quantconnect.com/tutorials/)
- [Python for Finance - DataCamp](https://www.datacamp.com/tracks/finance-fundamentals-in-python)

---



## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Deepak Kumar**

- GitHub: [@deepak338](https://github.com/deepak338)
- LinkedIn: [deepak-kumar-0c](https://www.linkedin.com/in/deepak-kumar-0c/)
- Portfolio: [bit.ly/deepak-portfolio-111](https://bit.ly/deepak-portfolio-111)
- Location: Jharkhand, Ranchi, India

---

## 🙏 Acknowledgments

- Yahoo Finance for providing free historical stock data
- The SciPy and NumPy communities for optimization tools
- Modern Portfolio Theory pioneers: Harry Markowitz and William Sharpe
- All open-source contributors whose libraries made this project possible

---

## 📞 Contact & Support

Have questions or suggestions? Feel free to:
- Open an issue on GitHub
- Connect with me on LinkedIn
- Email: deepakthedev@gmail.com



---

**Last Updated:** November 2024
