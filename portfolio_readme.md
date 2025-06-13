# 📊 Portfolio Optimization using Modern Portfolio Theory (MPT)

This project explores portfolio optimization using **Modern Portfolio Theory (MPT)**. It aims to calculate the optimal allocation of assets that maximizes return for a given level of risk using Python.

## 📁 Project Structure

```
portfolio-optimization/
├── opt_port.ipynb    # Jupyter notebook containing the code for data analysis, visualization, and optimization
└── README.md         # This file
```

## ⚙️ Features

- Fetch historical stock price data
- Calculate daily and annualized log returns
- Compute the covariance matrix
- Calculate portfolio expected return, volatility, and Sharpe Ratio
- Visualize efficient frontier
- Perform optimization to maximize Sharpe Ratio using scipy.optimize

## 🧪 Tech Stack

| Tool/Library | Purpose |
|--------------|---------|
| Python | Core programming language |
| Pandas | Data manipulation and analysis |
| NumPy | Numerical operations |
| Matplotlib | Data visualization |
| yfinance | Fetching historical financial data |
| SciPy | Optimization (minimize negative Sharpe) |

## 🧠 Optimization Method

- **Objective**: Maximize Sharpe Ratio
- **Constraints**:
  - Sum of weights = 1 (fully invested)
  - Weights between 0 and 1 (long-only portfolio)

## 📈 Visuals Included

- Efficient frontier
- Portfolio allocations
- Risk vs Return scatter plot

## 🚀 How to Run

1. Clone the repository or download the notebook.

2. Install required packages:
   ```bash
   pip install pandas numpy matplotlib yfinance scipy
   ```

3. Open the notebook:
   ```bash
   jupyter notebook opt_port.ipynb
   ```

4. Run the cells step by step.

## 🔍 Example Insights

- Optimal portfolio allocations
- Maximum Sharpe Ratio and associated weights
- Risk-return tradeoff analysis with visual plots

## 📋 Prerequisites

- Python 3.7 or higher
- Jupyter Notebook or JupyterLab
- Internet connection (for fetching stock data)

## 🤝 Contributing

Feel free to fork this project and submit pull requests for any improvements or additional features.

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

