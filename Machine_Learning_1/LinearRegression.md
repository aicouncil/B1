# Machine Learning 1: Concepts Covered in `ds_b1_ml_1.ipynb`

This notebook introduces foundational concepts in supervised machine learning, focusing on **Simple Linear Regression**, its mathematical underpinnings, and practical implementation. It also introduces the **Gradient Descent** optimization technique and presents a **case study** using real-world advertising data.

---

## 1. Simple Linear Regression (Type 1: Ordinary Least Squares)

### What is Simple Linear Regression?

Simple Linear Regression is a method to model the relationship between a single independent variable (feature) and a dependent variable (target) by fitting a linear equation to observed data. The model is:

\[
\hat{y} = w_0 + w_1 x
\]

Where:
- \(\hat{y}\): predicted value
- \(x\): input feature
- \(w_0\): intercept (bias)
- \(w_1\): slope (weight)

### Ordinary Least Squares (OLS) Approach

OLS finds the best-fitting line by minimizing the sum of the squared differences (errors) between actual and predicted values.

#### Example

Suppose you have data:

| X (input) | y (output) |
|-----------|------------|
|     3     |     4      |
|     5     |     8      |
|     9     |     9      |
|     7     |     6      |
|    10     |     9      |

#### Steps

1. **Visualize**  
   Scatter plot of X vs. y to see the relationship.

2. **Calculate slope and intercept**  
   - Slope (\(w_1\)):
     \[
     w_1 = \frac{\sum{(X_i - \bar{X})(y_i - \bar{y})}}{\sum{(X_i - \bar{X})^2}}
     \]
   - Intercept (\(w_0\)):
     \[
     w_0 = \bar{y} - w_1 \bar{X}
     \]
   - Example code:
     ```python
     n1 = ((X - X.mean()) * (y - y.mean())).sum()
     d1 = ((X - X.mean()) ** 2).sum()
     w1 = n1 / d1
     w0 = y.mean() - w1 * X.mean()
     ```

3. **Make Predictions**
   - \(\hat{y} = w_0 + w_1 X\)

4. **Plot the regression line**  
   Plot both the original data and the regression line for visualization.

5. **Predict for new data**  
   Example: For \(X=3.8\), plug into the equation to get \(\hat{y}\).

6. **Evaluate Error**  
   Calculate Mean Absolute Error (MAE):
   \[
   \text{MAE} = \frac{1}{n}\sum{|y_i - \hat{y}_i|}
   \]

---

## 2. Error Optimization: Gradient Descent (Type 2)

### What is Gradient Descent?

Gradient Descent is an iterative optimization algorithm used to minimize a loss function (error) by adjusting the model parameters in the opposite direction of the gradient.

#### Steps in Gradient Descent

1. **Initialize parameters**  
   Start with initial guesses for \(w_0\) and \(w_1\) (e.g., 2 and 1).

2. **Calculate predictions**  
   \(y_{pred} = w_0 + w_1 X\)

3. **Compute the error**  
   Mean Squared Error (MSE):
   \[
   \text{MSE} = \frac{1}{n}\sum{(y_i - y_{pred,i})^2}
   \]

4. **Compute gradients**  
   - For \(w_0\): \(\frac{\partial}{\partial w_0}\) of MSE
   - For \(w_1\): \(\frac{\partial}{\partial w_1}\) of MSE
   - Example code:
     ```python
     dew0 = -2 * (y - yh).mean()
     dew1 = -2 * ((y - yh) * X).mean()
     ```

5. **Update parameters**  
   Using a learning rate \(\eta\):
   \[
   w_0 = w_0 - \eta \cdot dew0
   \]
   \[
   w_1 = w_1 - \eta \cdot dew1
   \]

6. **Repeat**  
   Loop steps 2–5 for several iterations to minimize the error.

#### Example Output

- Each iteration prints the error, showing how the model improves.
- Final fitted parameters and predictions are visualized.

---

## 3. Case Study: Predicting Sales from Advertising Data

### Dataset

A real-world dataset with columns:
- `TV`: TV advertising budget
- `radio`: Radio advertising budget
- `newspaper`: Newspaper advertising budget
- `sales`: Sales figures

#### Data Loading and Exploration

```python
df = pd.read_csv('https://github.com/bipulshahi/Dataset/raw/refs/heads/main/Advertising.csv', index_col=0)
df.head()
```
Visualizes the first few rows and examines the relationship between features (e.g., TV budget) and sales with a scatter plot.

#### Building a Predictive Model

- Focuses on using `TV` as the feature to predict `sales`.
- Uses Gradient Descent to fit a linear regression model as described above.
- Tracks error across iterations to ensure model convergence.

#### Example Training Loop

```python
w0 = 6
w1 = 6.5
for i in range(50):
    yh = w0 + w1 * X
    error = ((y - yh)**2).mean()
    dew0 = -2 * ((y-yh)).mean()
    dew1 = -2 * ((y-yh)*X).mean()
    lr = 0.00001
    w0 = w0 - lr * dew0
    w1 = w1 - lr * dew1
    print(i, error)
```

Observes how error drops rapidly in early iterations and then stabilizes, indicating the model is learning.

---

## Summary

- **Simple Linear Regression (OLS)**: Analytical way to find the best-fit line for a single feature.
- **Gradient Descent**: Iterative method to minimize error and optimize model parameters.
- **Error Metrics**: Used Mean Absolute Error (MAE) and Mean Squared Error (MSE) to assess model performance.
- **Case Study**: Applied concepts to a real-world dataset, demonstrating practical model training and evaluation.

---

## Further Exploration

- Try using more features (`radio`, `newspaper`) for multiple linear regression.
- Experiment with different learning rates in gradient descent.
- Visualize residuals to further understand model fit.

---
