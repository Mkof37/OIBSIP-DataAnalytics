# L2-T1: Predicting House Prices with Linear Regression

This project builds and evaluates a linear regression model for predicting house prices from floor area, number of rooms, house age, and distance to the city centre. It demonstrates an end-to-end workflow from exploratory data analysis and preprocessing to model evaluation and interpretation.

## Project files

| File | Description |
| house_price_regression.ipynb | Jupyter notebook containing the analysis, model, diagnostics, and interpretation |
| house_prices_dataset.csv | Synthetic dataset with 10,000 rows and four numeric predictors plus the price target |

## Dataset features

| Column | Description |
| square_feet | House floor area in square feet |
| num_rooms | Number of rooms |
| age | House age in years |
| distance_to_city(km) | Distance from the city centre; used as a numeric proxy for location |
| price | House price to predict |

The dataset has no missing values, duplicate rows, or original categorical columns. It contains 38 non-positive prices (all negative), which are invalid for real house prices and are investigated in the notebook.

## Notebook workflow

The notebook covers:

1. Dataset loading and exploratory analysis, including null checks, descriptive statistics, and price distributions.
2. Feature selection reasoning for area, rooms, age, and distance to the city centre.
3. A leakage-safe preprocessing pipeline for numeric imputation and categorical imputation/One-Hot Encoding. The source data needs no imputation or encoding; a derived location-zone feature demonstrates One-Hot Encoding separately.
4. Correlation analysis and a correlation heatmap, plus a multicollinearity check.
5. An 80/20 train/test split and a scikit-learn Linear Regression model.
6. Evaluation with MSE, RMSE, MAE, and R².
7. Actual-versus-predicted and residual diagnostic plots.
8. Raw and standardized coefficient analysis.
9. A sensitivity analysis of the invalid-price handling.
10. A bonus comparison of Linear Regression, Ridge, and Lasso.

## Handling non-positive prices

The notebook investigates the 38 negative target values and finds that they occur among small, older houses farther from the city centre. The primary model excludes these invalid target rows and is evaluated on valid prices only. A sensitivity model adds the invalid rows to its training data, then scores both models on the same positive-price test rows.

For this reproducible split, the primary model uses 7,969 training rows and 1,993 test rows. Adding the invalid rows to training changes test R² from about 0.9551 to 0.9552 and RMSE from about 20,206 to 20,202. The notebook treats these as dataset-specific findings, not proof of how the data was generated.

## Results

On the held-out test set, the primary Linear Regression model reports:

- **R²:** approximately 0.955
- **RMSE:** approximately 20,206 price units
- **MAE:** approximately 16,263 price units

The residual diagnostics show errors centred close to zero with similar spread across predicted-price groups. The notebook also reports similar training and test scores for this split.

### Coefficients

Raw coefficients describe the estimated price change per one-unit increase in a feature, holding other features fixed:

- square_feet: approximately +149 per additional square foot
- num_rooms: approximately +20,100 per additional room
- age: approximately −1,001 per additional year
- distance_to_city(km): approximately −4,995 per additional kilometre

Because these features use different units, the notebook also compares standardized coefficients (price change per one standard deviation). In this dataset and split, floor area has the largest absolute standardized coefficient, followed by distance, number of rooms, and age. These are model associations, not causal effects.

### Regularized models

Ridge and Lasso achieve nearly the same test scores as ordinary Linear Regression. With four predictors and this dataset, regularization makes little difference, so the notebook retains Linear Regression as the simplest final model.

## Run the notebook

Install the required packages:

```bash
pip install numpy pandas scikit-learn matplotlib seaborn scipy jupyter
```

Start Jupyter from this folder and open `house_price_regression.ipynb`:

```bash
jupyter notebook
```

The notebook reads `house_prices_dataset.csv` using a relative path, so run it with this folder as the working directory.

## Limitations

- Distance to the city centre is only a proxy for location; the dataset has no neighbourhood or property-condition features.
- The data is synthetic, so its model performance should not be interpreted as expected accuracy on real housing transactions.
- The primary model excludes non-positive prices and is best supported for the remaining valid-price feature range, not necessarily for the low-price corner represented by those excluded rows.
