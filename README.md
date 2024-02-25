https://www.kaggle.com/competitions/store-sales-time-series-forecasting

score : 0.38532
leaderboard  : 41/703

# Sales Forecasting for Ecuadorian Stores

This project focuses on forecasting sales for 33 product families across 54 stores in Ecuador from August 16, 2017, to August 31, 2017. The code utilizes various Python libraries and Darts, a powerful tool for time series processing and forecasting.

## Data Sources and Preprocessing

Data is loaded from multiple CSV files:

- `train.csv`: Sales data with columns for date, store number, product family, sales, and promotions.
- `holidays_events.csv`: Information on holidays and events, including dates, types, locales, and descriptions.
- `stores.csv`: Store information, including city, state, type, and cluster.
- `oil.csv`: Daily oil prices.
- `transactions.csv`: Daily transaction counts per store.
- `test.csv` and `sample_submission.csv`: For submission to the forecasting competition.

Data preprocessing involves merging datasets, handling missing values, and converting categorical variables into one-hot encoded vectors. Sales data is transformed into `TimeSeries` objects for modeling.

## Covariates

Several covariates are considered for the forecasting models:

- **Time Covariates**: Attributes like year, month, day, day of the year, weekday, week of the year, and linear time steps.
- **Oil Covariates**: Moving averages of oil prices over 7, 14, and 28 days.
- **Holiday Covariates**: Indicators for various types of holidays and events.
- **Promotion Covariates**: Information on promotions and their moving averages over 7 and 28 days.
- **Transactions**: Historical transaction counts used as past covariates.

## Model Training and Forecasting

LightGBM models are trained for each product family using the prepared covariates. The models predict future sales, taking into account the specified covariates and transaction data. The forecasting process is encapsulated in functions to streamline training and prediction.

## Submission Preparation

Forecasted sales are inverse-transformed, aggregated, and cleaned to prepare a submission dataframe that matches the competition's requirements. Negative forecasts are set to zero to ensure realistic predictions.
