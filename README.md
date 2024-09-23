# Gold Price Time Series Analysis

## Project Overview

This project explores the application of various time series analysis techniques on gold prices using Python. The primary goal is to analyze and forecast gold prices based on historical data. Key concepts like trend decomposition, stationarity testing, autocorrelation, and ARIMA modeling are employed.

## Dataset

The dataset used for this project is extracted from a `.xls` file containing daily gold prices. The dataset includes the following columns:
- `Date`: Date of the observation
- `Open`: Opening price of gold for that day
- `High`: Highest price of gold for that day
- `Low`: Lowest price of gold for that day
- `Close`: Closing price of gold for that day
- `Change (Pips)`: Change in price in pips
- `Change (%)`: Percentage change in price

A new column, `Value`, representing the average of the opening and closing prices, is created for further analysis.

## Project Steps

### 1. Data Loading and Preprocessing
- Data is loaded from an `.xls` file and transformed into a pandas DataFrame.
- The `Date` column is parsed as a date, and a new `Value` column is created by averaging the `Open` and `Close` prices.
- Data is checked for null values and any inconsistencies.

### 2. Time Series Decomposition
- The time series is decomposed into its components (trend, seasonality, and residuals) using both additive and multiplicative models.
- This helps visualize the underlying patterns of the gold prices.

### 3. Stationarity Testing
- **ADF Test** (Augmented Dickey-Fuller Test) and **KPSS Test** (Kwiatkowski-Phillips-Schmidt-Shin) are conducted to test whether the gold price time series is stationary.
- The results of these tests guide further transformations like differencing and detrending to make the series stationary.

### 4. Detrending and Deseasonalizing
- The series is detrended using both the least squares fit and by subtracting the trend component from the decomposed time series.
- The series is deseasonalized by dividing the original series by the seasonal component.

### 5. Autocorrelation and Partial Autocorrelation
- Autocorrelation and Partial Autocorrelation plots are generated to examine the correlations at different lags.
- Lag plots are also created to visualize relationships between the current and lagged values of the series.

### 6. Forecastability Estimation
- **Approximate Entropy (ApEn)** and **Sample Entropy (SampEn)** are calculated to estimate the predictability and randomness of the gold price series.
- These metrics provide insight into the complexity and forecastability of the series compared to random datasets.

### 7. Granger Causality Test
- The Granger causality test is performed to examine if the `Month` variable can predict changes in gold prices, helping to assess relationships between variables.

### 8. ARIMA Model Building
- ARIMA (AutoRegressive Integrated Moving Average) models are constructed to forecast future gold prices.
- The order of differencing, AR, and MA terms are determined through visual inspection of ACF and PACF plots, as well as statistical tests.
- Various models are compared using AIC values to select the best-fitting model.

### 9. Model Validation and Forecasting
- The time series is split into training and testing sets, and the ARIMA model is used to forecast future prices.
- The model's performance is visualized by plotting the forecast against actual test values, with confidence intervals for prediction uncertainty.
- **Auto ARIMA** is also used to automate the model selection process and further fine-tune the forecasts.

## Key Libraries Used
- `pandas`: Data manipulation and analysis
- `numpy`: Mathematical functions
- `statsmodels`: Time series analysis (ARIMA, decomposition, stationarity tests, ACF, PACF, etc.)
- `scipy.signal`: Detrending functions
- `matplotlib`: Plotting
- `pmdarima`: Automatic ARIMA model fitting

## Usage Instructions

1. Install required dependencies:
   ```
   pip install pandas numpy statsmodels scipy pmdarima matplotlib
   ```

2. Load the dataset and preprocess it:
   - Ensure the `.xls` dataset file is in the correct path and read it into a pandas DataFrame.

3. Run each section of the analysis:
   - Time series decomposition, stationarity tests, detrending, and ARIMA model fitting can be executed step-by-step.
   
4. Evaluate the ARIMA model:
   - Compare different ARIMA models and visualize the forecast against actual values to assess the accuracy of the prediction.

## Results
- **Time Series Analysis**: The gold prices show clear trends and seasonal patterns.
- **Stationarity Tests**: Initial results indicate non-stationarity, necessitating differencing and detrending.
- **ARIMA Model**: An ARIMA(0,1,1) model was selected as the best model based on the lowest AIC value.
- **Forecasting**: The model effectively captures the general trend of gold prices but shows some variance in short-term predictions.

## Future Work
- Experiment with seasonal ARIMA models (SARIMA) to capture seasonal patterns more effectively.
- Incorporate exogenous variables, such as economic indicators, to improve forecasting accuracy.
- Explore deep learning models like LSTM for time series forecasting.

## Conclusion
This project demonstrates a comprehensive approach to time series analysis using gold prices as a case study. From decomposing the series into its components to fitting an ARIMA model for forecasting, various techniques were employed to analyze and predict future gold prices.

