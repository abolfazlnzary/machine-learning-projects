# Real Estate Price Prediction

An educational Machine Learning project for predicting house prices per unit area using Multiple Linear Regression.

## Target

- House price per unit area

## Available Features

- Transaction date
- House age
- Distance to the nearest MRT station
- Number of convenience stores
- Latitude
- Longitude

## Project Status

In progress

## Run locally

Use Python 3.13 and run the following commands from the project directory:

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m jupyter notebook
```

Open `house_price_regression.ipynb`, select the project environment, and run the cells in order.

## Data and attribution

414 observations and six predictive features. The `No` column is an identifier and is excluded from training.
The target is price per unit area, measured in 10,000 New Taiwan dollars per ping; this is not total house price.

Source: Yeh, I. (2018). *Real Estate Valuation* [Dataset]. UCI Machine Learning Repository.
https://doi.org/10.24432/C5J30W

Dataset license: [Creative Commons Attribution 4.0](https://creativecommons.org/licenses/by/4.0/).
The CSV is a local conversion of the source Excel dataset; the original Excel file is included in `data/`.

## Current results

LinearRegression with an 80/20 random split (`random_state=42`): 331 training samples and 83 test samples.

| Metric | Test result |
| --- | ---: |
| MAE | 5.3052 |
| MSE | 53.5023 |
| RMSE | 7.3145 |
| R-squared | 0.6811 |
| Training-mean baseline MAE | 10.9167 |

R-squared is not classification accuracy. Results describe this particular split and are not a guarantee for other locations or time periods.

## Limitations and next steps

This is an educational project using historical data from a limited geographic area.
Some feature relationships are nonlinear, and location features are correlated.
Residual analysis and the final project conclusion are still in progress.
