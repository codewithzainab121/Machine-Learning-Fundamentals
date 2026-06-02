
# 📁 supervised_learning.md

## Introduction

Supervised learning is one of the main types of machine learning where:
The model learns from labeled data (input + correct answer).

📌 You give the model:

* Questions (input features)
* Answers (labels / target)

The model’s job:
👉 learn the pattern between them
👉 then predict answers for new questions

Supervised learning is mainly divided into two categories:

* Regression
* Classification

---

# 🔹 Regression

## What is Regression?

Regression is a method used to predict a continuous value based on the relationship between dependant variable & one or more independant variables.

👉 In plain terms:
It answers questions like “If this changes, what will happen to that?”

Example:
If study hours increase, what will be the expected marks?

One of the most common regression algorithms is Linear Regression.

---

## Linear Regression

Linear regression is a method used to find the relationship between a dependent variable and one or more independent variables by drawing a straight line that best fits the data.

In linear regression, the relationship is continuous.

👉 In simple terms:
It helps you predict a value (like marks) based on another value (like study hours).

y = mx + b

y = dependant variable , what you predict : output
m = slope (change rate)
x = independant variable , input
b = intercept (starting value)

---

## Train-Test Split

To train a machine learning model properly, we split the dataset into training data and testing data.

It randomly splits your data into 2 parts:

* Training data → used to learn
* Testing data → used to check performance

Core Concept:

| Step       | Data Used        |
| ---------- | ---------------- |
| Training   | X_train, y_train |
| Prediction | X_test           |
| Evaluation | y_test vs y_pred |

If you want SAME split every time:
Use:
`random_state=42`

Once the model is trained, we need a way to measure how well it performs.

---

## Mean Squared Error (MSE)

The average of squared differences between actual values and predicted values.

🔍 What it means in plain English:

1. Take actual value (y)
2. Take predicted value (ŷ)
3. Find error = (y − ŷ)
4. Square it
5. Take average of all errors

MSE is the loss function that measures how wrong the model is, and the model’s goal is to minimize it.

🔹 “Loss” = error, mistake, how wrong the model is
🔹 “Function” = a formula that calculates that error

🧩 So together:
Loss function = a formula that tells the model how wrong it is

MSE = \frac{1}{n}\sum (y-\hat{y})^2

For Linear Regression:
So MSE actually depends on:
👉 m (slope)
👉 b (intercept)

The model tries to minimize this error using optimization techniques.

---

## Ordinary Least Squares (OLS)

OLS tries to minimize the error between your predicted values and actual values.

The sum of squared errors:

\sum (actual\ value - predicted\ value)^2

For small datasets, Ordinary Least Squares can directly calculate the best parameters.

However, for larger and more complex datasets, optimization algorithms like Gradient Descent are preferred.

---

## Gradient Descent

Gradient Descent = how we minimize error step by step.

Gradient Descent uses the slope(change rate) of MSE to adjust model parameters and reduce prediction error step by step.

🚀 Gradient Descent enters

The model asks:
“How should I change m and b to reduce MSE?”

This is where gradients (slopes of error) come in.

📈 We calculate:

* How MSE changes when m changes
* How MSE changes when b changes

👉 This gives direction:

* increase?
* decrease?

| OLS                         | Gradient Descent            |
| --------------------------- | --------------------------- |
| Uses mathematical equations | Starts with random values   |
| Gives answer in one shot    | Slowly adjusts step-by-step |
| Formula-based               | Moves toward minimum error  |

---

## R-Squared (R²)

R² measures how much of the variation in output your model explains.

It checks the strength of the relationship between variables in Linear Regression.

R² can be:

* Between 0 and 1
* Negative (bad model)

Examples:

* R² = 0.9 → model explains 90% of data
* R² = 0 → model explains nothing
* R² < 0 → model is worse

Linear Regression also assumes that input features are not highly dependent on each other.

---

## Multicollinearity

Multicollinearity happens when:
Two or more independent features are highly correlated with each other.

We should minimize multicollinearity so our model can be more accurate.

Example:

| Height (cm) | Height (inches) | Weight |
| ----------- | --------------- | ------ |
| 170         | 66.9            | 65     |
| 180         | 70.8            | 75     |

Here:

* Height (cm) and Height (inches) are almost the same thing
* So they are highly correlated

### Correlation Matrix

A correlation matrix shows how strongly features are related to each other.

| Value | Meaning                      |
| ----- | ---------------------------- |
| +1    | Perfect positive correlation |
| 0     | No relationship              |
| -1    | Perfect negative correlation |

Correlation = “are these two related?”

However, correlation only measures relationships between two variables at a time.

To detect deeper feature redundancy, we use Variance Inflation Factor (VIF).

### Variance Inflation Factor (VIF)

It measures:
How much multicollinearity exists in your features.

VIF = “is this feature redundant because of all others?”

| VIF Value | Meaning                   |
| --------- | ------------------------- |
| 1         | No correlation            |
| 1 – 5     | Moderate                  |
| > 5       | High correlation          |
| > 10      | Serious multicollinearity |

Suppose:

* A not strongly correlated with B
* A not strongly correlated with C

BUT:
👉 A = combination of B and C

Correlation matrix ❌ might miss it
VIF ✅ will catch it

---

## Multiple Linear Regression (MLR)

When linear regression uses more than one independent variable, it becomes Multiple Linear Regression.

MLR = multiple independent variables predicting one dependent variable.

---

## Feature Scaling

Feature scaling is used to bring all features into a similar range.

Why it matters:
If one feature is much larger than another, it can dominate the model.

Common methods:

* StandardScaler
* MinMaxScaler

Feature scaling is especially important for:

* Gradient Descent
* Distance-based algorithms

---

## Overfitting vs Underfitting

A good model should generalize well to unseen data.

Two common problems during training are underfitting and overfitting.

### Underfitting

Happens when the model is too simple and cannot capture the real pattern in the data.

It performs poorly on both training and testing data.

### Overfitting

Happens when the model learns the training data too well, including noise and irrelevant details.

It performs very well on training data but poorly on new data.

🔥 Example:

* Underfitting student:
  Barely studied → fails everywhere

* Overfitting student:
  Memorized past papers → fails when questions change

---

# 🔹 Classification

## What is Classification?

Classification is used when the output belongs to categories.

Examples:

* spam or not spam
* fraud or not fraud
* rain or no rain

One of the most widely used classification algorithms is Logistic Regression.

---

## Logistic Regression

Logistic Regression is a supervised classification model.

Unlike Linear Regression, Logistic Regression predicts probabilities instead of continuous values.

It classifies values into categories.

Examples:

* email → spam or not
* transaction → fraud or not

---

## Sigmoid Function

Sigmoid is a function that converts any number into a value between 0 and 1.

Input:
any real number

Output:
always between 0 and 1

\sigma(x)=\frac{1}{1+e^{-x}}

---

## Threshold

Threshold = decision boundary for classification.

Logistic Regression gives probability between 0 and 1.

Now we need to make a decision:

* If probability ≥ threshold → Class 1
* If probability < threshold → Class 0

Default threshold:
0.5

---

## Cross Entropy Loss

Cross Entropy measures:
“How wrong your predicted probabilities are from actual values.”

Cross Entropy is a loss function used in classification problems.

Instead of predicting numbers,
classification models predict probabilities.

Case 1:

* Actual = 1
* Predicted = 0.9
  Loss = small

Case 2:

* Actual = 1
* Predicted = 0.1
  Loss = very large

After training the classifier, we evaluate its performance using classification metrics.

---

## Classification Evaluation Metrics

### predict()

The model makes predictions on unseen data.

Input:
X_test

Output:
y_pred

---

### Accuracy Score

Percentage of correct predictions.

Accuracy = Correct Predictions / Total Predictions

---

### Confusion Matrix

| Actual / Predicted | 0  | 1  |
| ------------------ | -- | -- |
| 0                  | TN | FP |
| 1                  | FN | TP |

* TN → correctly predicted 0
* TP → correctly predicted 1
* FP → predicted 1 but actually 0
* FN → predicted 0 but actually 1

---

### Precision

Precision = TP / (TP + FP)

When model predicts positive,
how often is it correct?

---

### Recall

Recall = TP / (TP + FN)

Out of all actual positives,
how many did we catch?

---

### F1-Score

Balance between precision and recall.

---

### Support

Number of actual samples in each class.

---

## Data Preprocessing

### Column Transformer

Column Transformer is used to apply different preprocessing steps to different columns.

Example:

* Scale numerical columns
* Encode categorical columns

It helps create clean preprocessing pipelines for machine learning models.
