# Decision Tree Classifier Tutorial

This tutorial provides a detailed walkthrough on using decision trees for classification problems using Python's `scikit-learn` library. We'll focus on two popular datasets: the Iris dataset and the Wine dataset. The content includes explanations, code examples, and visualizations to make the concepts clear and practical.

---

## 1. Introduction to Decision Trees

A **Decision Tree** is a supervised machine learning algorithm used for both classification and regression tasks. It splits the data into branches to make decisions based on the input features.

**Advantages:**
- Easy to understand and visualize.
- Requires little data preprocessing.
- Can handle numerical and categorical data.

**Disadvantages:**
- Prone to overfitting.
- Can be unstable with small variations in data.

---

## 2. Exploring the Iris Dataset

The Iris dataset is a classic dataset in machine learning, containing measurements of different iris flowers. Here’s how to load and explore it:

```python
import pandas as pd

# Load the dataset
df = pd.read_csv('https://raw.githubusercontent.com/bipulshahi/Dataset/refs/heads/main/Iris.csv')
print(df.head())
```

**Sample Output:**
```
   Id  SepalLengthCm  SepalWidthCm  PetalLengthCm  PetalWidthCm      Species
0   1            5.1           3.5            1.4           0.2  Iris-setosa
1   2            4.9           3.0            1.4           0.2  Iris-setosa
2   3            4.7           3.2            1.3           0.2  Iris-setosa
3   4            4.6           3.1            1.5           0.2  Iris-setosa
4   5            5.0           3.6            1.4           0.2  Iris-setosa
```

---

## 3. Data Preprocessing

Before training, split the features (`X`) and target (`y`), and then separate the data into training and test sets.

```python
from sklearn.model_selection import train_test_split

X = df[['SepalLengthCm', 'SepalWidthCm', 'PetalLengthCm', 'PetalWidthCm']]
y = df['Species']

xtrain, xtest, ytrain, ytest = train_test_split(X, y, test_size=0.25, random_state=42)
```

- **Features (`X`)**: Sepal and petal measurements.
- **Target (`y`)**: Species of iris.

---

## 4. Training a Decision Tree Classifier

We'll use `DecisionTreeClassifier` from `scikit-learn` and limit the tree depth to avoid overfitting.

```python
from sklearn.tree import DecisionTreeClassifier

# Initialize the classifier with a maximum depth
model = DecisionTreeClassifier(max_depth=2)
model.fit(xtrain, ytrain)
```

---

## 5. Visualizing the Decision Tree

Visualizing helps understand how the tree splits data at each node.

```python
import matplotlib.pyplot as plt
from sklearn.tree import plot_tree

plt.figure(figsize=(16, 10))
plot_tree(model, feature_names=xtrain.columns, class_names=model.classes_, filled=True)
plt.show()
```

![Decision Tree Example](https://scikit-learn.org/stable/_images/sphx_glr_plot_tree_classification_001.png)

---

## 6. Evaluating Model Performance

Assess your model's accuracy on both training and test sets:

```python
print("Training accuracy:", model.score(xtrain, ytrain))
print("Test accuracy:", model.score(xtest, ytest))
```

**Example Output:**
```
Training accuracy: 0.96
Test accuracy: 0.97
```
- High accuracy on both sets indicates a well-generalized model.

---

## 7. Applying Decision Tree to the Wine Dataset

Let’s try another dataset to reinforce our understanding.

**Load the Wine Dataset:**

```python
df_wine = pd.read_csv('https://raw.githubusercontent.com/bipulshahi/Dataset/refs/heads/main/wine.csv')
print(df_wine.head())
```

**Sample Output:**
```
   alcohol  malic_acid   ash  alcalinity_of_ash  ...  proline  Target
0    14.23        1.71  2.43              15.6  ...     1065       0
1    13.20        1.78  2.14              11.2  ...     1050       0
...
```

**Train a Decision Tree on Wine Data:**

```python
X_wine = df_wine.drop('Target', axis=1)
y_wine = df_wine['Target']

xtrain_w, xtest_w, ytrain_w, ytest_w = train_test_split(X_wine, y_wine, test_size=0.25, random_state=42)

model_wine = DecisionTreeClassifier(max_depth=3)
model_wine.fit(xtrain_w, ytrain_w)

print("Wine dataset accuracy:", model_wine.score(xtest_w, ytest_w))
```

---

## 8. Key Takeaways

- Decision trees are powerful and interpretable models for classification.
- Always split your data to avoid overfitting and to fairly evaluate your model.
- Visualizations help in interpreting the decision process.
- Try different datasets and tune parameters (like `max_depth`) for optimal results.

---

## 9. Further Reading

- [scikit-learn Decision Trees Documentation](https://scikit-learn.org/stable/modules/tree.html)
- [Iris Dataset Description](https://archive.ics.uci.edu/ml/datasets/iris)
- [Wine Dataset Description](https://archive.ics.uci.edu/ml/datasets/wine)

---

Happy Learning!
