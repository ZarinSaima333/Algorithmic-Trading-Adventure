# Algorithmic Trading Adventure 📈

A Python-based algorithmic trading project that implements the **Golden Cross/Death Cross** trading strategy to simulate stock market investments. This project demonstrates how to leverage technical analysis indicators to make automated trading decisions.

## 🎯 Project Overview

**Alex's Challenge**: Starting with a $5,000 budget, develop a trading tool that uses moving averages to identify profitable entry and exit points in the stock market. The goal is to implement a class-based approach for flexibility and scalability.

## 📊 Strategy: Golden Cross Trading

The strategy implemented in this project is based on two key technical indicators:

- **Golden Cross**: When the 50-day moving average crosses **above** the 200-day moving average → **BUY signal** (bullish trend)
- **Death Cross**: When the 50-day moving average crosses **below** the 200-day moving average → **SELL signal** (bearish trend)

## 🛠️ Technologies Used

- **Python 3.x**
- **yfinance**: For downloading historical stock market data
- **pandas**: For data manipulation and analysis
- **matplotlib**: For data visualization

## 📋 Features

1. **Class-Based Architecture**: Encapsulates trading logic in a reusable `AlgorithmicTrader` class
2. **Historical Data Analysis**: Downloads and processes stock data from Yahoo Finance
3. **Data Cleaning**: Removes duplicates and handles missing values
4. **Technical Indicators**: Calculates 50-day and 200-day moving averages
5. **Automated Trading Logic**:
   - Identifies golden cross opportunities
   - Calculates maximum shares within budget
   - Executes buy/sell decisions
   - Prevents simultaneous positions
   - Force-closes positions at the end of the period
6. **Performance Tracking**: Calculates profits/losses and tracks all trades

## 🚀 Installation

```bash
pip install yfinance pandas matplotlib
```

## 💻 Usage

### Basic Example

```python
from Algorithmic_Trading_Adventure import AlgorithmicTrader

# Initialize the trader
trader = AlgorithmicTrader(
    symbol="AAPL",           # Stock ticker symbol
    start_date="2018-01-01", # Start date for analysis
    end_date="2023-12-31",   # End date for analysis
    capital=5000             # Starting capital (default: $5000)
)

# Run the trading strategy
trader.run()
```

### Class Methods

- `fetch_data()`: Downloads historical stock data from Yahoo Finance
- `clean_data()`: Removes duplicates and handles NaN values
- `compute_indicators()`: Calculates 50-day and 200-day moving averages
- `execute_strategy()`: Implements the golden cross/death cross trading logic
- `evaluate()`: Calculates the profit or loss
- `run()`: Executes the complete trading pipeline

## 📈 Example Results

Running the strategy on Apple (AAPL) stock from 2018 to 2023:

```
Final Cash: $16,268.63
Profit/Loss: $11,268.63

Trades:
(Timestamp('2019-05-06'), 'BUY', 49.77, 100)
(Timestamp('2022-06-03'), 'SELL', 142.78, 100)
(Timestamp('2022-09-26'), 'BUY', 148.28, 96)
(Timestamp('2022-10-07'), 'SELL', 137.78, 96)
(Timestamp('2023-03-22'), 'BUY', 155.72, 85)
(Timestamp('2023-12-29'), 'FORCE SELL', 190.73, 85)
```

**Performance**: +225% return over the 6-year period

## 📊 Visualization

The project includes visualization capabilities to plot:
- Stock closing prices
- 50-day moving average
- 200-day moving average

```python
import matplotlib.pyplot as plt

plt.figure(figsize=(14,6))
plt.plot(trader.data["Close"], label="Close Price", alpha=0.7)
plt.plot(trader.data["MA50"], label="MA 50")
plt.plot(trader.data["MA200"], label="MA 200")
plt.title("Golden Cross Strategy - AAPL")
plt.legend()
plt.show()
```

## ⚠️ Important Notes

1. **Budget Constraints**: The algorithm respects the initial capital limit and calculates the maximum number of shares affordable
2. **Position Limits**: Only one position can be held at a time (no buying while already in a position)
3. **Force Close**: Any open position is automatically closed on the last day of the analysis period
4. **Data Quality**: The system handles duplicate data and forward-fills NaN values


## ⚖️ Disclaimer

**This is an educational project for learning purposes only.** Past performance does not guarantee future results. This tool should not be used for actual trading without proper risk assessment and understanding of financial markets. Always consult with financial professionals before making investment decisions.

## 📝 License

This project is created for educational purposes. Feel free to use and modify for learning.

## 🙏 Acknowledgments

- Yahoo Finance for providing historical stock data
- The Python data science community for excellent libraries
- Technical analysis principles from traditional trading theory

---

**Happy Trading! 🚀** Remember: *"The market can remain irrational longer than you can remain solvent."* - John Maynard Keynes
