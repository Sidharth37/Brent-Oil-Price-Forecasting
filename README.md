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
