# Stock-Analysis
Python-based analysis of Tesla stock prices using pandas, matplotlib, and Plotly. Includes visualization of closing prices along with 50-day and 200-day moving averages for trend analysis.
import pandas as pd
import matplotlib.pyplot as plt
import plotly.graph_objects as go

# Read data
file_path = r'C:\Users\HP ELITEBOOK 830 G5\OneDrive\Desktop\stockmar\tesla.csv'
data = pd.read_csv(file_path)

# Show first few rows to verify
print(data.head())
print(data.columns)
print(data.dtypes)

# Convert 'Date' to datetime
data['Date'] = pd.to_datetime(data['Date'])

# Calculate Moving Averages
data['MA50'] = data['Close'].rolling(window=50).mean()
data['MA200'] = data['Close'].rolling(window=200).mean()

# Matplotlib plot
plt.figure(figsize=(10, 5))
plt.plot(data['Date'], data['Close'], label='Close', color='blue')
plt.plot(data['Date'], data['MA50'], label='MA50', color='orange')
plt.plot(data['Date'], data['MA200'], label='MA200', color='green')
plt.title('Tesla Stock - Closing Price and Moving Averages')
plt.xlabel('Date')
plt.ylabel('Price')
plt.legend()
plt.tight_layout()
plt.show()
