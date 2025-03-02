# Prophet forecasting model
Using Prophet machine learning model to forecast stock prices

# ETF Analysis with PySpark

## Project Overview
This project demonstrates an ETF (Exchange-Traded Fund) trading strategy analysis using PySpark. The analysis focuses on the VTI ETF, leveraging technical indicators like moving averages to generate trading signals, evaluate performance through backtesting, and forecast future prices. The workflow includes data collection, preprocessing, signal generation, profit analysis, and visualization.

### Key Features
- **Data Collection**: Fetch 5 years of VTI ETF historical data using `yfinance`.
- **Data Preprocessing**: Clean and prepare data with PySpark.
- **Signal Generation**: Calculate 10-day and 100-day moving averages to generate buy/sell signals.
- **Profit Analysis**: Backtest hypothetical returns based on crossover signals.
- **Visualization**: Plot closing prices and moving averages using `matplotlib`.

## Business Objectives
1. **Optimize ETF Trading Strategies**: Use moving average crossovers for decision-making.
2. **Backtesting**: Evaluate signal effectiveness.
3. **Forecasting**: Inform long-term investment strategies.

---

## Technologies Used
- **PySpark**: Distributed data processing.
- **pandas/yfinance**: Data fetching and manipulation.
- **matplotlib**: Visualization.
- **Jupyter Notebook**: Interactive analysis.

---

## Installation
### Dependencies
```bash
pip install pyspark pandas yfinance matplotlib
Setup
Download Data:

##python
import yfinance as yf
ticker = "VTI"
end_date = date.today()
start_date = end_date - timedelta(days=5*365)
df = yf.download(ticker, start=start_date, end=end_date)
df.to_csv(f'{ticker}_stock_data.csv', index=True)
Initialize PySpark:

##python

from pyspark.sql import SparkSession
spark = SparkSession.builder.appName("ETF_Analysis").getOrCreate()
sdf = spark.createDataFrame(df.reset_index())
Code Structure
Data Collection & Preprocessing:

Fetch VTI data using yfinance.

Clean column names and convert to PySpark DataFrame.

##Moving Averages & Signals:

Calculate 10-day and 100-day moving averages.

Generate signals (1 for buy, -1 for sell, 0 for hold).


##Signal Analysis:

Count signal distribution.

Calculate hypothetical returns from signals.

Visualization:

Plot closing prices and moving averages.

Results
Signal Distribution
Signal	Count
0	10
-1	271
1	975
Profit Analysis
Signal	Buy Profit	Sell Profit
0	0.0	0.0
-1	0.0	-25.95
1	155.37	0.0
Closing Price vs Moving Averages

How to Run
Please go ahead and execute the Jupyter notebook final_python.ipynb.

Adjust the ticker variable to analyze other ETFs.

Modify window sizes (e.g., 10-day/100-day MA) in the signal generation step.

Contributions
Contributions are welcome! Open an issue or submit a pull request for:

Additional technical indicators (e.g., RSI, MACD).

Enhanced backtesting frameworks.

Machine learning integration for forecasting.


