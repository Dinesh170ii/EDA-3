# Shopify Stock Market Data Analysis

Overview

This project performs Exploratory Data Analysis (EDA) on Shopify stock market data using Python.

The analysis focuses on historical stock prices, trading volume, daily price changes, daily returns, and identification of unusual trading-volume days.

The project is implemented using Python, Pandas, NumPy, and Matplotlib in Google Colab/Jupyter Notebook.

Objectives

- Analyze historical Shopify stock price data.
- Understand the structure and characteristics of the dataset.
- Check for missing values.
- Convert the date column into a proper datetime format.
- Calculate daily price changes and daily returns.
- Analyze trading volume.
- Identify anomalous days based on unusually high trading volume.
- Calculate basic statistical measures.

 Dataset

The dataset is stored in:

`shopify_stock.xlsx`

Dataset Size

- **Rows:** 2,469
- **Columns:** 7

 Dataset Columns

| Column | Description |
|---|---|
| `date` | Date of the stock trading |
| `open` | Opening stock price |
| `high` | Highest stock price during the day |
| `low` | Lowest stock price during the day |
| `close` | Closing stock price |
| `adj_close` | Adjusted closing stock price |
| `volume` | Number of shares traded |
Technologies Used

- Python 3
- Pandas
- NumPy
- Matplotlib
- Google Colab / Jupyter Notebook
- Excel

#Data Analysis Performed

 1. Importing Libraries

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
```

 2. Loading the Dataset

```python
df = pd.read_excel("shopify_stock.xlsx")
```

3. Dataset Inspection

The project examines the first few records, dataset shape, column information, and descriptive statistics.

 4. Date Conversion

```python
df["date"] = pd.to_datetime(df["date"], utc=True)
```

 5. Missing Value Analysis

```python
df.isnull().sum()
```

The analysis shows no missing values in the dataset.

 6. Sorting Data

```python
df = df.sort_values("date")
```

 Feature Engineering

### Daily Price Change

```python
df["Date_delta"] = df["close"] - df["open"]
```

### Daily Percentage Change

```python
df["Daily_delta"] = ((df["close"] - df["open"]) / df["open"]) * 100
```

### Daily Returns

```python
df["Daily_returns"] = ((df["close"] - df["open"]) / df["open"]) * 100
```

 Trading Volume Analysis

| Metric | Value |
|---|---:|
| Average Volume | 16,570,491.78 |
| Maximum Volume | 208,959,000 |
| Minimum Volume | 1,039,000 |

 Anomaly Detection

An anomalous trading day is identified when trading volume is greater than two times the average trading volume.

```python
threshold = 2 * average_volume
anomalous_days = df[df["volume"] > threshold]
```

The analysis identified **215 anomalous days** using this threshold.

## Statistical Analysis

| Statistic | Value |
|---|---:|
| Mean Return | 0.0864 |
| Variance | 9.7331 |
| Standard Deviation | 3.1198 |

##  Key Findings

- The dataset contains 2,469 Shopify stock records.
- There are no missing values.
- Stock prices vary considerably over the analyzed period.
- Trading volume varies significantly between trading days.
- 215 days were identified as anomalous based on the selected volume threshold.
- The calculated mean daily return is approximately 0.0864%.
- The standard deviation of the calculated daily returns is approximately 3.12%.

## Project Structure

```text
Shopify-Stock-Analysis/
├── shopify_stock.xlsx
├── Untitled6 (1).ipynb
└── README.md
```


##  Conclusion

This project demonstrates how Python can be used to perform stock market data analysis. The analysis covers data inspection, date processing, missing-value checking, feature creation, trading-volume analysis, anomaly detection, and statistical analysis of daily returns.

The project provides a foundation for further work such as stock-price visualization, trend analysis, volatility analysis, and predictive modeling.

##  Author

**Ramya J**

BCA Student
