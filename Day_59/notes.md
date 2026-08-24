# Stochastic Gradient Descent (SGD)

Stochastic Gradient Descent (SGD) is an optimization algorithm used to minimize the loss function of a machine learning model. It updates the model parameters using **one training sample at a time** instead of using the entire dataset.

## How SGD Works

```text
Training Data
     ↓
Shuffle Data
     ↓
Select One Sample
     ↓
Make Prediction
     ↓
Calculate Loss
     ↓
Calculate Gradient
     ↓
Update Parameters
     ↓
Next Sample
     ↓
Repeat for Multiple Epochs
```

## Gradient Descent Update

The general update rule is:

```text
θ = θ - η × gradient
```

Where:

* `θ` = model parameter
* `η` = learning rate
* `gradient` = direction of the loss function

For Linear Regression:

```text
ŷ = wx + b

w = w - η × dw
b = b - η × db
```

## Batch GD vs SGD

| Batch Gradient Descent        | Stochastic Gradient Descent  |
| ----------------------------- | ---------------------------- |
| Uses all samples              | Uses one sample              |
| One update after full dataset | Update after every sample    |
| Smooth convergence            | Noisy convergence            |
| Expensive for large datasets  | Efficient for large datasets |
| Higher computation per update | Lower computation per update |

## Example

For:

```text
X = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]
```

SGD processes the samples individually:

```text
Sample 1 → Prediction → Gradient → Update
Sample 2 → Prediction → Gradient → Update
Sample 3 → Prediction → Gradient → Update
...
```

After several epochs, the model learns parameters close to:

```text
w ≈ 2
b ≈ 0
```

## Implementation From Scratch

```python
import numpy as np

X = np.array([1, 2, 3, 4, 5], dtype=float)
y = np.array([2, 4, 6, 8, 10], dtype=float)

w = 0.0
b = 0.0

learning_rate = 0.01
epochs = 100

for epoch in range(epochs):

    # Shuffle samples
    indices = np.random.permutation(len(X))

    for i in indices:

        x_i = X[i]
        y_i = y[i]

        # Prediction
        y_pred = w * x_i + b

        # Error
        error = y_pred - y_i

        # Calculate gradients
        dw = 2 * x_i * error
        db = 2 * error

        # Update parameters
        w -= learning_rate * dw
        b -= learning_rate * db

print("Weight:", w)
print("Bias:", b)
```

## Learning Rate

The learning rate controls how large each update is.

```text
Too Large
    ↓
Overshooting / Unstable Training

Too Small
    ↓
Very Slow Training

Suitable
    ↓
Faster and Stable Convergence
```

## Epoch

An **epoch** means the model has processed the complete training dataset once.

If there are 100 samples and 10 epochs:

```text
100 samples × 10 epochs
= approximately 1000 SGD updates
```

## Advantages

* Efficient for large datasets
* Low computation per update
* Lower memory requirement
* Frequent parameter updates
* Suitable for online learning
* Useful for large-scale machine learning

## Disadvantages

* Noisy parameter updates
* Loss may fluctuate
* Sensitive to learning rate
* Can take longer to settle
* Requires hyperparameter tuning

## SGD vs Mini-Batch GD

```text
Batch GD
→ Entire dataset

Mini-Batch GD
→ Small group of samples

SGD
→ One sample
```

Mini-Batch Gradient Descent is commonly used in deep learning because it provides a good balance between speed and stable gradient estimation.

## Key Takeaways

* SGD stands for **Stochastic Gradient Descent**.
* It uses **one sample per parameter update**.
* It is useful for large datasets.
* Data is commonly shuffled before training.
* The learning rate controls the update size.
* SGD is faster per update but more noisy than Batch Gradient Descent.
* Mini-Batch Gradient Descent is a practical middle ground.

## Git Commands

```bash
git add .
git commit -m "Add Stochastic Gradient Descent from scratch"
git push origin main
```
