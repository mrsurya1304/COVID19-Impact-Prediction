# COVID19-Impact-Prediction
- Forecasting the impact of the COVID 19 virus across India and using it to suggest the risk for touring a certain place. 
- We have data from https://data.covid19india.org/csv/latest/districts.csv.
- It contains the amount of confirmed, recovered and deceased cases across all districts of India on a daily basis from 26-Apr-2020 to 31-10-2021
- We can use this time series data of 1.5 years to attempt to forecast the impact of covid on a near future date

# Algorithms used
1. Prophet from Facebook
2. Holt- Winters Exponential Smoothing

# The COVID-19_Impact_Forecast.ipynb 
- Contains the gathering of data from the URL
- Shows how the data has been manipulated and grouped for further processing
- Plots the time series data to important variables to see the relationship between them
- Performs appropriate dimentionality reduction to retain the features which we most need
- Checks for stationarity of data with rolling mean, rolling standard deviation and Augmented Dickey-Fuller (ADF) test
- Determines the appropriate algorithms to use (FB Prophet and Holt-Winters)
- Performs both algorithms, fits the models, forecasts trend for 3 months in the future, plots, compares and picks out the better algorithm.
- In this case Holt-Winters Double Exponential Smoothing, Additive model with Weekly seasonality gives the best forecasts

# The COVID-19_Touring_Risk_Prediction.ipynb
- Now we know the best algorithm to forecast COVID 19 impact
- This notebook attempts to write code with more modularity with functions so it could be used repetitively
- plotting method takes in a data frame and uses a line plot to plot the variables.
- Assignrisk method takes in a data frame and assigns the risk and its category by a custom defined function which (Confirmed cases on that day/Maximum confirmed cases for that district)*95
- This function ensures maximum risk possible is 95%. It appends the risk and risk category and returns the data frame.
- The risk category is divided into intervals of 20% ranging from Low to Very High risk
- The getdata function takes in a district name and a past date and finds the amount of confiremed cases on the queried past date by just extracting it from the dataset
- The forecast method takes in a district name and a future date and applies the Holt-Winters model and plots the past trend and future forecast
- It also returns the possible number of confirmed cases, the predicted risk percentage and category of risk to the user
- From this information the user can decide a safe time or a safe place for touring.

# Conclusion
- The notebooks are self explanatory and if you do get lost there are many comments which guide you along the way.
- The algorithm and script in COVID-19_Touring_Risk_Prediction.ipynb is what is used in my COVID Encyclopedia android app to predict touring risk.
- These notebooks are the more extended implementations with more visualization and intuition behind how I came to a decision on which trend forecasting algorithm to choose for my app
