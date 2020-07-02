# Subset Selection and Regularization

## Subset Selection

Feature selection - choose a subset of features, then fit model

### Method 1a: try everything \(simplest\)

Simplest version: for every possible subset of features S, fit the model on these features, to get a fitted model Ms.

### Method 1b: try everything \(slightly sophisticated\)

Fix k = 1,2,3,...p, and fit all possible models that have exactly k features. Pick the best of these models using some criterion. Now you have M0, M1, …, Mp, so choose the best model using a validation set or cross-validation\).

### Method 2a: Forward stepwise selection / 2b: Backward stepwise selection

Forward: starting with intercept-only model and add a feature each time

Backward: starting with full model and remove a feature each time

两种方法，第一种运算量极大但能够确保找到best model；第二种不保证能找到best model但是运算比较可实现。

### Standard

![](../../.gitbook/assets/image%20%28129%29.png)

Don’t select a subset of features based on p-values! Unimportant features may appear important, and vice-versa.

Also, don’t select features based on individual correlations with the target variable.

## Regularization

So far, so good. But our goal now is not just find to find the best \[ i.e., the coefficients that minimize on the training data \] We would also like these coefficients to not get too crazy, or maybe we’d like some of the coefficients to be zero. Therefore, we add constraints to coefficients. Meanwhile, it is to avoid overfitting.

![](../../.gitbook/assets/image%20%28127%29.png)

"[https://towardsdatascience.com/ridge-and-lasso-regression-a-complete-guide-with-python-scikit-learn-e20e34bcbf0b](https://towardsdatascience.com/ridge-and-lasso-regression-a-complete-guide-with-python-scikit-learn-e20e34bcbf0b)"

### Ridge Regression

Ridge regression shrinks the coefficients and it helps to reduce the model complexity and multi-collinearity. _Lower the constraint \(low λ\) on the features, the model will resemble linear regression model._

### Lasso Regression

 Lasso regression not only helps in reducing over-fitting but it can help us in feature selection.

![](../../.gitbook/assets/image%20%28128%29.png)

### Code

```text
library(glmnet)
# prepare data
x <- model.matrix(outcome ~ cuisine + borough + month + weekday, training_set)[,-1]
y <- training_set$outcome

# fit lasso and ridge regressions
ridge <- glmnet(x, y, family = "binomial", alpha = 0, lambda = 0.01)
lasso <- glmnet(x, y, family = "binomial", alpha = 1, lambda = 0.01)
```

Codes should refer to "[https://github.com/SueShen7/coursesnyu/blob/master/analysis.R](https://github.com/SueShen7/coursesnyu/blob/master/analysis.R)". It's a little complicated since a specific package is used and there is requirement for data structure.

Example

![](../../.gitbook/assets/image%20%28130%29.png)

