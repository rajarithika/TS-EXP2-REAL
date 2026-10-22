# EXPERIMENT 2: TIME SERIES ANALYSIS AND DECOMPOSITION

**Name:** RAJA RITHIKA M

**Reg. No.:** 2305001029

## 1. Aim

To perform time series analysis and decomposition on the monthly average temperature of a city using Python.

## 2. Software Required

- Python 3
- Google Colab or Jupyter Notebook
- Pandas
- Matplotlib
- Statsmodels

## 3. Procedure

1. Import the required libraries.
2. Create monthly temperature data.
3. Convert the month column into a time index.
4. Plot the original time series.
5. Decompose the time series into trend, seasonal, and residual components.
6. Plot and display each component.
7. Observe the results.

## 4. Program

```python
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Create monthly temperature data
months = [
    "Jan", "Feb", "Mar", "Apr", "May", "Jun",
    "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"
]

temperature = [
    25, 27, 29, 32, 34, 33,
    32, 31, 30, 29, 27, 25
]

# Create DataFrame
data = pd.DataFrame({
    "Month": months,
    "Temperature": temperature
})

print("Monthly Temperature:")
print(data)

# Convert month into a time index
data["Month"] = pd.date_range(
    start="2025-01-01",
    periods=12,
    freq="ME"
)

data.set_index("Month", inplace=True)

print("\nTime Series Data:")
print(data)

# Plot the original time series
plt.figure(figsize=(10, 5))

plt.plot(
    data.index,
    data["Temperature"],
    marker="o"
)

plt.title("Monthly Average Temperature")
plt.xlabel("Month")
plt.ylabel("Temperature (°C)")
plt.grid()
plt.show()

# Perform time series decomposition
result = seasonal_decompose(
    data["Temperature"],
    model="additive",
    period=12
)

# Plot all decomposition components
result.plot()
plt.show()

# Display individual components
plt.figure()
plt.plot(result.observed)
plt.title("Observed Temperature")
plt.show()

plt.figure()
plt.plot(result.trend)
plt.title("Trend Component")
plt.show()

plt.figure()
plt.plot(result.seasonal)
plt.title("Seasonal Component")
plt.show()

plt.figure()
plt.plot(result.resid)
plt.title("Residual Component")
plt.show()

# Print decomposition components
print("\nTrend:")
print(result.trend)

print("\nSeasonal:")
print(result.seasonal)

print("\nResidual:")
print(result.resid)
```

## 5. Expected Output

- Monthly average temperature graph.
<img width="1050" height="587" alt="image" src="https://github.com/user-attachments/assets/86631a4f-521e-4a67-94b1-559ea357e7d2" />

- Observed temperature component.
<img width="782" height="143" alt="image" src="https://github.com/user-attachments/assets/d06bb59f-86e1-4eda-bdfb-06ad2a726111" />

- Trend component.
<img width="786" height="155" alt="image" src="https://github.com/user-attachments/assets/815a98cd-765b-4ad8-8ebd-d8b2ad6d5735" />

  
- Seasonal component.
<img width="778" height="152" alt="image" src="https://github.com/user-attachments/assets/4fd30b61-d29d-4a0b-bde8-1e6158e1c309" />

 
- Residual component.
 <img width="786" height="173" alt="image" src="https://github.com/user-attachments/assets/85ccb6e5-6f13-4827-a184-bfe320027548" />



## 6. Observation

The monthly temperature increases until May and then gradually decreases towards December. The decomposition separates the observed data into trend, seasonal, and residual components.

## 7. Result

Thus, the monthly temperature time series was successfully plotted and decomposed into observed, trend, seasonal, and residual components using Python.
