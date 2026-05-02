# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 02-05-2026

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### SOFTWARE REQUIRED:
  google colab
### DATASET:
 Walmart_sales.csv
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
NAME:Thejashree S
REGNO: 212224240175
```
```py
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
data=pd.read_csv('/content/Walmart_Sales.csv')
data = data['Weekly_Sales'].values

N=len(data)
#Define lags
lags = range(35)

#Pre-allocate autocorrelation table
autocorr_values = []
#Mean of the data
mean_data = np.mean(data)
#variance of the data
variance_data = np.var(data)
#Normalize the data
normalized_data = (data - mean_data) / np.sqrt(variance_data)

#Go through lag componenets one-by-one
for lag in lags:
  if lag == 0:
    autocorr_values.append(1)
  else:
    auto_cov = np.sum((data[:-lag] - mean_data) * (data[lag:] - mean_data)) / N
    autocorr_values.append(auto_cov / variance_data)

#display the graph
plt.figure(figsize=(10,6))
plt.stem(lags,autocorr_values)
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.title('Autocorrelation Function')
plt.grid(True)
plt.show()
```

### OUTPUT:

<img width="1203" height="701" alt="image" src="https://github.com/user-attachments/assets/cfa549b4-7e13-4a42-9e64-1bc9008d50f1" />


### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
