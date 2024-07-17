# Weather-Forecast
The project forecasts weather by applying ARIMA model in order to accurately predict the parameters of temperature, relative humidity, wind gusts, and wind direction. To forecast the weather parameters, we first checked for missing values and performed a non-parametric interpolation “spline” to impute the missing values. Later on, we sought to reduce the number of observations by selecting the fifth observation from our series because weather parameters are not poised to change a lot during the hour. The points
were reduced to 69924 observations from 349622. Afterward, we built an ARIMA model for the prediction of daily weather parameters separately.
## Augmented Dickey-Fuller Test
The Augmented Dickey-Fuller (ADF) test's null hypothesis is that the time series is nonstationary. Therefore, you reject the null hypothesis and conclude that the time series isstationary if the test's p-value is less than the significance level (0.05). As a result, we can infer that the time series is stationary in our situation because all of the parameters' P-Values fell below 0.05.
## Forecasting Relative Humidity
The data was converted into a time series and plotted using R software. A random trend in the temperature recordings was noted in the plot. There was no visible seasonality or linearity on the plot but the data had missing values which were interpolated using a non-parametric measure called “spline”. We reduced the observations to 7283 observations for easier analysis by taking an interval of 4 hours.
![Screenshot 2024-07-17 170035](https://github.com/user-attachments/assets/59f0dd69-a362-4a9b-952b-2a23ae81e5b1)
## Time Series Decomposition
Using the decompose() function in R, we were able to remove the seasonality, and trend components in the series for further analysis.
![Screenshot 2024-07-17 170139](https://github.com/user-attachments/assets/0da0432d-6735-4923-b63d-4ba044dc7720)
## Identifying A Possible Arima Model
To build the model, we selected the 48th observation after an interval of 5 observations for analysis since no major changes were expected during that time. The points were reduced to 69924 observations from 349622. An appropriate ARIMA model order was sought after using the auto.arima() function, the values of p, d, and q for an ARIMA(p,d,q) were determined. The function combines unit root testing, MLE minimization, and AIC to provide the best ARIMA model. The ideal model was determined to be ARIMA( )with the lowest AIC. ARIMA(5,0,0)(2,1,1)[6] was the model we settled on. 
![Screenshot 2024-07-17 170436](https://github.com/user-attachments/assets/cd3c78c8-9967-46fe-a234-24a4f449eae3)
## Residual Plot
We can see from the plot of the standardized residuals which indicates that there’s no trend inthe residuals, no extraordinary values(outliers), and no change in variance over time. The Autocorrelation function plot of the residuals does not portray the existence of significant autocorrelations which is a good factor. The Q-Q plot is a normal probability plot, so the assumption of normally distributed residuals is right. The last plot indicates p-values for the Ljung-Box-Pierce statistics for each lag up to 20 and most p-values fall above the dashed blue line which is a good indicator of a good model. 
![Screenshot 2024-07-17 170614](https://github.com/user-attachments/assets/0c31788f-36df-4aa7-ad7f-8ca41fc625a4)
The same was done for other parameters. Please refer to this link for further analysis https://drive.google.com/file/d/1EhrSrvAC6GAqIAuRdbccmSq2lU0ho7u3/view?usp=sharing.
