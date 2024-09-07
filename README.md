### NAME: KARTHIKEYAN R
### Reg.No: 212222240046
### Date: 
# Ex.No:04   FIT ARMA MODEL FOR TIME SERIES
### AIM:
To implement ARMA model in python.
### ALGORITHM:
1. Import necessary libraries.
2. Set up matplotlib settings for figure size.
3. Define an ARMA(1,1) process with coefficients ar1 and ma1, and generate a sample of 1000
   data points using the ArmaProcess class.
4. Plot the generated time series and set the title and x-axis limits.
5. Display the autocorrelation and partial autocorrelation plots for the ARMA(1,1) process using
   plot_acf and plot_pacf.
6. Define an ARMA(2,2) process with coefficients ar2 and ma2, and generate a sample of 10000
    data points using the ArmaProcess class.
7. Plot the generated time series and set the title and x-
   axis limits.
8. Display the autocorrelation and partial autocorrelation plots for the ARMA(2,2) process using
  plot_acf and plot_pacf.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.arima_process import ArmaProcess
from statsmodels.graphics.tsaplots import plot_acf, plot_pacf
data = pd.read_csv('/content/Gold Price.csv')
print(data.head())
```
```
production = data['Price'].dropna() # Changed 'price' to 'Price'
ar1 = np.array([1, -0.5])  # AR(1) coefficient
ma1 = np.array([1, 0.5])   # MA(1) coefficient
arma11_process = ArmaProcess(ar1, ma1)
arma11_sample = arma11_process.generate_sample(nsample=len(production))
ar2 = np.array([1, -0.5, 0.25])  # AR(2) coefficients
ma2 = np.array([1, 0.4, 0.3])    # MA(2) coefficients
arma22_process = ArmaProcess(ar2, ma2)
arma22_sample = arma22_process.generate_sample(nsample=len(production))
plt.figure(figsize=(14, 8))
plt.subplot(221)
plot_acf(arma11_sample, lags=20, ax=plt.gca(), title='ACF of Simulated ARMA(1,1)')
plt.subplot(222)
plot_pacf(arma11_sample, lags=20, ax=plt.gca(), title='PACF of Simulated ARMA(1,1)')
plt.subplot(223)
plot_acf(arma22_sample, lags=20, ax=plt.gca(), title='ACF of Simulated ARMA(2,2)')
plt.subplot(224)
plot_pacf(arma22_sample, lags=20, ax=plt.gca(), title='PACF of Simulated ARMA(2,2)')
plt.tight_layout()
plt.show()
```
### OUTPUT:
#### SIMULATED ARMA(1,1) PROCESS:
Partial Autocorrelation
![image](https://github.com/user-attachments/assets/f30145c0-e9f2-4f8a-8e24-047a23460bd2)

Autocorrelation
![image](https://github.com/user-attachments/assets/634da3f1-cd15-49df-a66b-e4f2e7b7f582)

##### SIMULATED ARMA(2,2) PROCESS:

Partial Autocorrelation
![image](https://github.com/user-attachments/assets/7b8c8224-8260-4461-b981-d6b465203b33)

Autocorrelation
![image](https://github.com/user-attachments/assets/ae8be3c7-121c-4031-8cee-f2ff1bc995b8)

### RESULT:
Thus, a python program is created to fit ARMA Model successfully.
