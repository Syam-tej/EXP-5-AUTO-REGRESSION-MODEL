# EXP-5-AUTO-REGRESSION-MODEL

## AIM:
Implementation of Auto Regression Model using Python

## ALGORITHM:
1.Import necessary libraries
2.Read the CSV file into a DataFrame
3.Perform Augmented Dickey-Fuller test
4.Split the data into training and testing sets.Fit an AutoRegressive (AR) model with 13 lags
5.Plot Partial Autocorrelation Function (PACF) and Autocorrelation Function (ACF)
6.Make predictions using the AR model.Compare the predictions with the test data
7.Calculate Mean Squared Error (MSE).Plot the test data and predictions.
## PROGRAM:
```
PYTHON import pandas as pd import numpy as np from matplotlib import pyplot from statsmodels.tsa.ar_model import AutoReg df=pd.read_csv("rainfall.csv") df X=df['temp'] X X.plot() from statsmodels.tsa.stattools import adfuller dtest=adfuller(X,autolag='AIC') print("ADF:",dtest[0]) print("P value:",dtest[1]) print("No. of lags:",dtest[2]) print("No. of observations used for ADF regression:",dtest[3]) X_train=X[:len(X)-15] X_test=X[len(X)-15:] AR_model=AutoReg(X_train,lags=13).fit() print(AR_model.summary()) from statsmodels.graphics.tsaplots import plot_pacf,plot_acf pacf=plot_pacf(X,lags=25) acf=plot_acf(X,lags=25) pred=AR_model.predict(start=len(X_train),end=len(X_train)+len(X_test)-1,dynamic=False) pred.plot() X_test pred import sklearn.metrics mse=sklearn.metrics.mean_squared_error(X_test,pred) mse**0.5 X_test.plot() pred.plot()
```
## OUTPUT:
## GIVEN DATA
![image](https://github.com/Syam-tej/EXP-5-AUTO-REGRESSION-MODEL/assets/93427224/6bf0131f-7057-428c-912a-3daa0ebc2336)

## PACF - ACF
![image](https://github.com/Syam-tej/EXP-5-AUTO-REGRESSION-MODEL/assets/93427224/365f275d-ca1e-40e6-84a1-dc665455809c)

## PREDICTION
![image](https://github.com/Syam-tej/EXP-5-AUTO-REGRESSION-MODEL/assets/93427224/663ed1f3-51bd-44c3-b18d-122a6eafee1e)

## FINIAL PREDICTION
![image](https://github.com/Syam-tej/EXP-5-AUTO-REGRESSION-MODEL/assets/93427224/e8bb2581-bf72-443e-b2ae-dcc79d2c70f5)

## RESULT:
Thus we have successfully implemented the auto regression function using above mentioned program.
