# Brent-Oil-Price-Forecasting
Machine learning Model to forecast Brent Oil prices for 90 days, based on historical data.<br>
<b>Business Case?</b><br>
Oil is the biggest predominant source of power, fueling the US and global economy. Fluctuation in oil prices affect industries around the globe.
Brent Oil pricing index, is used by the OPEC(Organization of Petroleum Exporting Countries) as a benchmark to set it's prices. Given these circumstances it becomes increasingly important for industries all around the world, but even more for oil importing organizations in countries where oil mining is not practiced.<br><br>
<b>The project is divided in 6 main parts:</b><br>
1. Importing the dataset<br>
2. Forecasting using FaceBook's Prophet model<br>
3. Cross Validation using FaceBook's Prophet model<br>
4. Data preprocessing for Arima model<br>
5. Forecasting using Arima model<br>
6. Evaluating the best model for forecasting<br><br>

<b>Importing the dataset -</b><br>
This is the simplest part of all, the data is imported from a CSV file with perfectly clean data. It has data for each day from May 20, 1987 to September 30, 2019. It compromises of 8216 records in all. Each record is made up of 2 attributes, date attribute and the price value for that particular day. Minimal manipulation is required, to conver the date field into a standard format, for both Facebook's Prophet and Arima model.<br><br>
<b>Forecasting using FaceBook's Prophet model -</b><br>
There are minimum data pre-processing requirement for the Prophet model, the data field should be in the data-time format and the column name should be ds, the other variable which we are trying to forecast the value for needs to be named 'y'.<br>
Initially we start by adding the time frame for which we want to forecast to the existing data frame. In our case it is 90 days. At this stage there is no corresponding price values for this duration. After this stage, the predict function is used to forecast for this interval.<br>
We obtained 3 important terms from the output of the prediction, yhat(actual forecasted value), yhatupper(upper limit of the forecast), yhatlowe(lower limit of the forecast). Based on the forecast we see a stable but slightly downward trend for the 90 day interval which were trying to forecast for.<br><br>
<b>Cross Validation using FaceBook's Prophet model -</b><br>
Over here  our main aim is to understand how well our model is performing. We run the FB prophet across time ranges based on initial load value and forecast horizon to understand the performance of the model. Based on the results obtained at this stage we find the RMSE(Root mean square error) value in the range of 16.8 to 19.6<br><br>
<b>Data preprocessing for Arima model</b><br>
The constraint for using the Arima model is you need to have the date time-time field as the index of the data frame. Also you need to make the series stationary before feeding it to the Arima model. Stationary series is time series with no visible trend and seasonality.
We first started by visualizing the time series data we have. We see an obvious trend. To get rid of this trend we use the differencing method, i.e. subtracting value at each day point by its previous day point. At the end of this step we get a series which looks non stationary on the first glance. To verify our assumption we carry out the AD Fuller test. Based on results of the AD Fuller, we confirm that the new formed series after differencing is indeed stationaty and go on to feeding this data to the model.<br><br>
<b>Forecasting using Arima model -</b><br>
Before we fit the model, we need to determine the values of p, d & q. The value of d is the number of differencing operations we have done, in our case 1. To determine the values of p(Number of autoregressive lags) and q(number of moving average lags) we use the ACF(Auto Correlation function) plot and PACF(Partial Auto Correlation function) plot. In our case we determine the values of p & q as one itself. Once all these parameters are determined we simply fit the model and start forecasting. The results of forecast for the 90 day time period was relatively stable, with a sligh upwards trend.<br><br>
<b>Evaluating the best model for forecasting</b><br>
We choose the best model based on the least RMSE(Root Mean Square Error) values. for the first model(FB Prophet) the RMSE is in the range of 16.8 to 19.6, for the Arima model the RMSE is 12.05, based on what we see the ARIMA model has a better forecasting performance as compared to the FB prophet model.
