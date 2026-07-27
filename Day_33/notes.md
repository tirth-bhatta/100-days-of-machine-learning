# Handling Mixed Variables | Feature Engineering

## 📌 What are Mixed Variables?

Mixed variables are datasets containing **different types of features** together, such as:

- Numerical (Age, Salary)
- Categorical (Gender, City)
- Date & Time (Joining Date)
- Text (Reviews)

Since ML models mainly work with numbers, each type must be processed differently before training.

---

## Example Dataset

| Age | Gender | City | Joining Date |
|-----:|--------|------|--------------|
| 25 | Male | Kathmandu | 2024-01-15 |
| 30 | Female | Pokhara | 2023-08-10 |

---

## How to Handle Mixed Variables

### 1. Numerical Features
- Handle missing values
- Scale or normalize data

Example:
```text
Age → StandardScaler()
```

### 2. Categorical Features
Convert text into numbers using:
- One-Hot Encoding
- Label Encoding
- Ordinal Encoding

Example:
```text
Male → 1
Female → 0
```

### 3. Date Features
Extract useful information like:
- Year
- Month
- Day
- Weekday

Example:
```text
2024-01-15 → Year=2024, Month=1
```

### 4. Text Features
Convert text into numerical vectors using:
- Bag of Words
- TF-IDF

---

## Using ColumnTransformer

```python
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import StandardScaler, OneHotEncoder

preprocessor = ColumnTransformer([
    ("num", StandardScaler(), ["Age"]),
    ("cat", OneHotEncoder(), ["Gender", "City"])
])
```

---

## Advantages
- Handles multiple data types together
- Keeps preprocessing organized
- Works well with ML Pipelines

## Disadvantages
- Slightly more preprocessing
- Different features need different techniques

---

## Key Takeaways

- Mixed variables contain different feature types.
- Numerical → Scaling
- Categorical → Encoding
- Date → Feature Extraction
- Text → Vectorization
- **ColumnTransformer** helps preprocess all feature types in one pipeline.