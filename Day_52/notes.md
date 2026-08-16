# Regression Metrics | MSE, MAE & RMSE | R² Score & Adjusted R² Score

Regression metrics are used to evaluate the performance of a regression model by comparing the actual values with the predicted values.

## 1. Mean Absolute Error (MAE)

MAE calculates the average absolute difference between actual and predicted values.

### Formula
MAE = (1/n) Σ |yᵢ - ŷᵢ|

- Easy to understand.
- Less sensitive to outliers than MSE.
- The error is in the same unit as the target variable.
- Lower MAE indicates better performance.

## 2. Mean Squared Error (MSE)

MSE calculates the average of the squared differences between actual and predicted values.

### Formula
MSE = (1/n) Σ (yᵢ - ŷᵢ)²

- Large errors are heavily penalized.
- More sensitive to outliers.
- The result is in squared units.
- Lower MSE indicates better performance.

## 3. Root Mean Squared Error (RMSE)

RMSE is the square root of MSE.

### Formula
RMSE = √MSE

- Penalizes large errors.
- Easier to interpret than MSE.
- Has the same unit as the target variable.
- Lower RMSE indicates better performance.

## 4. R² Score

R², or Coefficient of Determination, measures how much of the variation in the target variable is explained by the regression model.

### Formula
R² = 1 - (SSres / SStot)

Interpretation:
- R² = 1 → Perfect prediction
- R² = 0 → Model performs like predicting the mean
- R² < 0 → Model performs worse than the mean prediction

A higher R² generally indicates a better model.

## 5. Adjusted R² Score

R² can increase when unnecessary features are added to a model. Adjusted R² solves this problem by applying a penalty for adding extra predictors.

### Formula
Adjusted R² = 1 - [(1 - R²)(n - 1) / (n - p - 1)]

Where:
- n = Number of observations
- p = Number of independent variables
- R² = R² Score

Adjusted R² increases when a new feature improves the model significantly and can decrease when unnecessary features are added.

## Quick Comparison

| Metric | Better Value | Outlier Sensitivity |
|--------|--------------|---------------------|
| MAE | Lower | Low |
| MSE | Lower | High |
| RMSE | Lower | High |
| R² | Higher | High |
| Adjusted R² | Higher | High |

## Key Takeaways

- MAE measures the average absolute prediction error.
- MSE squares errors and strongly penalizes large errors.
- RMSE is the square root of MSE and remains in the target variable's unit.
- R² measures how much variation is explained by the model.
- Adjusted R² considers the number of features in the model.
- Lower MAE, MSE and RMSE indicate better performance.
- Higher R² and Adjusted R² generally indicate better performance.

#MachineLearning #Regression #ML #DataScience #Python