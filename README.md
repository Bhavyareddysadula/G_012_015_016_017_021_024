#COMPUTATIONAL SEQUENTIAL MODELING
Assignment – Option 1

Group Name: G_012_015_016_017_021_024 [MTech]

Jyothi Narsini				SE23MAID012

Sadula Gnana Bhavya Sri		SE23MAID015

Yasaswi Vanarasi			SE23MAID016

Yempathi Aashritha			SE23MAID017

Himavanth Jeevanigaa		SE23MAID021

Vikas Paspula				SE23MAID024



Group Contribution:

1.	Himavanth Jeevanigaa (SE23MAID021):
   
o	Contributed to data collection and preprocessing, including handling missing values and performing stationarity checks.

o	Drafted sections of the report related to data preprocessing and the importance of stationarity.

2. Sadula Gnana Bhavya Sri (SE23MAID015):
   
o	Focused on the ARIMA model development.

o	Conducted ACF/PACF analysis to select model parameters.

o	Prepared training and testing datasets for ARIMA and evaluated its performance.

3.	Yasaswi Vanarasi (SE23MAID016):
   
o	Worked on designing and implementing the LSTM model.

o	Prepared data sequences and ensured proper scaling for LSTM training.

o	Designed the architecture of the LSTM network and trained the model.

4.	Yempathi Aashritha (SE23MAID017):
   
o	Conducted exploratory data analysis and created visualizations, such as ACF/PACF plots and model comparison graphs.

o	Assisted with the hybrid model integration, focusing on combining ARIMA and LSTM outputs using weighted averages.

o	Contributed to the evaluation and interpretation of metrics like MAE and RMSE.

5.	Jyothi Narsini (SE23MAID012):
   
o	Led the development of the hybrid ARIMA-LSTM model.

o	Designed the weighted averaging methodology to combine outputs effectively.

o	Evaluated the hybrid model’s performance and prepared comparative analyses.

o	Assisted in creating visualizations comparing predictions of ARIMA, LSTM, and the hybrid model.

6.	Vikas Paspula (SE23MAID024):
   
o	Contributed to report writing, especially the introduction and conclusion sections.

o	Reviewed and edited the entire report for coherence and clarity.

o	Ensured that technical content was well-documented and organized.

 
Hybrid ARIMA-LSTM Model for Stock Price Forecasting
Introduction
In this report, we describe how we built a hybrid forecasting model combining ARIMA and LSTM to predict daily stock prices. Stock price prediction is challenging because prices often show trends, seasonality, and random patterns. ARIMA works well with trends and seasonality, while LSTM handles complex patterns like sudden price spikes. By combining both, we aimed to improve prediction accuracy.

Step 1: Data Collection and Preprocessing
1.	Data Collection:
o	We used daily Apple (AAPL) stock price data from Yahoo Finance (January 2015 to December 2023).
o	The closing price was our main feature, representing the stock’s value at the end of each trading day.
2.	Preprocessing Steps:
o	Missing Values: Missing values in the data were filled using interpolation.
o	Stationarity Check: Using the Augmented Dickey-Fuller (ADF) test, we found the data to be non-stationary (ADF Statistic: 0.19141, p-value = 0.9718).
o	Differencing: Since stationarity is essential for ARIMA, we applied differencing, which removes trends.
Why is this important?
Non-stationary data has trends and patterns that make modelling difficult. Differencing ensures the data is stable over time.

Step 2: ARIMA Model (Short-Term Trends)
1.	Understanding ARIMA:
ARIMA uses three parameters:
o	AR (p): Autoregression, the relationship between current and past values.
o	I (d): Differencing, which removes trends.
o	MA (q): Moving Average, the relationship between current value and past residual errors.
2.	Parameter Selection:
We used Auto-Correlation Function (ACF) and Partial Auto-Correlation Function (PACF) plots to choose ARIMA parameters. The best combination was ARIMA(1,1,1).
3.	Model Training and Testing:
o	Training Data: 80% of the data.
o	Testing Data: 20% of the data.
o	The model was trained to capture short-term trends.
4.	ARIMA Results:
o	ARIMA performed well in predicting short-term patterns. However, it struggled with sudden price spikes and non-linear patterns.

Step 3: LSTM Model (Long-Term Patterns)
1.	Why LSTM?
Long Short-Term Memory (LSTM) networks are great for time series data because they can "remember" long-term dependencies.
2.	Data Preparation:
o	Normalization: We scaled the data to a range between 0 and 1 to help the LSTM learn better.
o	Rolling Windows: Data was split into sequences of 60 time steps (input) and 1 time step (output).
3.	LSTM Architecture:
o	Layers:
	LSTM Layer 1: 50 units with return sequences.
	Dropout: 20% to reduce overfitting.
	LSTM Layer 2: 50 units without return sequences.
	Dense: Final layer for prediction.
o	Optimizer: Adam, which adjusts learning rates.
o	Loss Function: Mean Squared Error (MSE).
4.	Training:
o	Epochs: 50
o	Batch Size: 32
5.	LSTM Results:
o	LSTM captured non-linear patterns better than ARIMA but needed help with trends.

Step 4: Hybrid Model (Combining ARIMA and LSTM)
1.	Why Combine?
ARIMA captures trends, while LSTM learns complex patterns. Combining them makes predictions stronger.
2.	Combination Method:
o	Weighted Average: We assigned weights to ARIMA and LSTM outputs based on their accuracy.
o	This approach ensured that both models contributed effectively.
3.	Evaluation Metrics:
o	Mean Absolute Error (MAE): Measures average errors.
o	Root Mean Squared Error (RMSE): Measures large errors more heavily.

Step 5: Visualizations
1.	ACF/PACF Plots: Showed lagged correlations and helped us decide ARIMA parameters.
2.	Model Predictions: Plots compared ARIMA, LSTM, and Hybrid forecasts against actual stock prices.
   
Key Insights from Plots:

•	ARIMA was accurate for smooth trends but missed sudden changes.

•	LSTM captured sharp spikes but sometimes overfitted.

•	The hybrid model performed the best, balancing short-term and long-term accuracy.


Conclusion
The hybrid ARIMA-LSTM model worked better than standalone models because it used the strengths of both:

•	ARIMA captured short-term patterns.

•	LSTM captured non-linear dependencies.

•	The hybrid model gave the lowest prediction error, making it the best choice for stock price forecasting.








