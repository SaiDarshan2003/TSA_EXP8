## Ex.No: 08 MOVING AVERAGE MODEL AND EXPONENTIAL SMOOTHING
### Date: 
### AIM:
To implement Moving Average Model and Exponential smoothing Using Python.
### ALGORITHM:
1. Import necessary libraries
2. Read the electricity time series data from a CSV file,Display the shape and the first 20 rows of
the dataset
3. Set the figure size for plots
4. Create a new figure for plotting,Plot the original data and fitted value
5. Show the plot
### PROGRAM:
```
# Import necessary libraries
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import warnings
from statsmodels.tsa.holtwinters import ExponentialSmoothing
warnings.filterwarnings('ignore')
data = pd.read_csv('/content/sales.csv')
data['Date'] = pd.to_datetime(data['Date'], format='%m/%d/%Y')
data.set_index('Date', inplace=True)
adj_close_data = data[['Adj Close']]
print("Shape of the dataset:", adj_close_data.shape)
print("First 5 rows of the dataset:")
print(adj_close_data.head())
plt.figure(figsize=(12, 6))
plt.plot(adj_close_data['Adj Close'], label='Original Adj Close Data', color='blue')
plt.title('Original Adjusted Close Prices')
plt.xlabel('Date')
plt.ylabel('Adjusted Close Price (USD)')
plt.legend()
plt.grid()
plt.show()
rolling_mean_10 = adj_close_data['Adj Close'].rolling(window=10).mean()
plt.figure(figsize=(12, 6))
plt.plot(adj_close_data['Adj Close'], label='Original Adj Close Data', color='blue')
plt.plot(rolling_mean_10, label='Moving Average (window=10)', color='orange')
plt.title('Moving Average of Adjusted Close Prices')
plt.xlabel('Date')
plt.ylabel('Adjusted Close Price (USD)')
plt.legend()
plt.grid()
plt.show()
model = ExponentialSmoothing(adj_close_data['Adj Close'], trend='add', seasonal=None)
model_fit = model.fit()
predictions = model_fit.predict(start=len(adj_close_data), end=len(adj_close_data) + 30)
plt.figure(figsize=(12, 6))
plt.plot(adj_close_data['Adj Close'], label='Original Adj Close Data', color='blue')
plt.plot(predictions, label='Exponential Smoothing Forecast', color='orange')
plt.title('Exponential Smoothing Predictions for Adjusted Close Prices')
plt.xlabel('Date')
plt.ylabel('Adjusted Close Price (USD)')
plt.legend()
plt.xticks(rotation=45)
plt.grid(True)
plt.tight_layout()
plt.show()
```

### OUTPUT:

![image](https://github.com/user-attachments/assets/f427be4e-ac2f-499d-8047-7d7c5e880395)

Moving Average

![image](https://github.com/user-attachments/assets/15ed736a-1175-41b4-b283-5acf5e54c772)

Plot Transform Dataset

![image](https://github.com/user-attachments/assets/333aaf99-909e-4424-b1b3-6aaa4f3a57b7)


Exponential Smoothing

![image](https://github.com/user-attachments/assets/2b14bcf0-7fe8-41e2-95f9-40cad6181f32)


### RESULT:
Thus, implemention of the Moving Average Model and Exponential smoothing using python is successful.
