# Multiple Linear Regression | Part 3 | Code From Scratch

import numpy as np
from sklearn.datasets import load_diabetes
from sklearn.model_selection import train_test_split
from sklearn.metrics import r2_score

# Load data
data = load_diabetes()
X = data.data
y = data.target

# Split data
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

class MultipleLinearRegression:

    def fit(self, X, y):
        X = np.c_[np.ones(X.shape[0]), X]

        # Calculate coefficients
        beta = np.linalg.inv(X.T @ X) @ X.T @ y

        self.intercept_ = beta[0]
        self.coef_ = beta[1:]

    def predict(self, X):
        return self.intercept_ + np.dot(X, self.coef_)


# Train model
model = MultipleLinearRegression()
model.fit(X_train, y_train)

# Prediction
y_pred = model.predict(X_test)

# Results
print("Intercept:", model.intercept_)
print("Coefficients:", model.coef_)
print("R2 Score:", r2_score(y_test, y_pred))

print("\nActual:", y_test[:5])
print("Predicted:", y_pred[:5])