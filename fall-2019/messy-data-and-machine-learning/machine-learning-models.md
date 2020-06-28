---
description: Lecture 4 - 6
---

# Machine Learning Models

## KNN

```text
library(class)
training_pred <- knn(training_tweets_aug %>% select(-text,-author), 
                     training_tweets_aug %>% select(-text,-author), 
                     cl = training_tweets_aug$author,
                     k = 5,
                     prob = FALSE)
testing_pred <- knn(training_tweets_aug %>% select(-text,-author), 
                     testing_tweets_aug %>% select(-text,-author), 
                     cl = training_tweets_aug$author,
                     k = 5,
                     prob = FALSE)
```

‒ Non-parametric ‒ Discriminative \(cannot simulate data\) ‒ Good at binary and multiclass classification ‒ Works best with a lot of data ‒ Need to tune the parameter K

## Logistic Regression

```text
res <- glm(Y~X1+X2, data=data, family=binomial(link="logit"))
summary(res)
p = predict(model3,poll_data_full,type='response') # probability
```

‒ Discriminative \(cannot simulate data\) ‒ Good at binary classification ‒ Weak assumptions ‒ Good with discrete and continuous features ‒ Widely used and easy to interpret. This should be one of your go-to methods.

## Naive Bayes

Generative \(can simulate data\) ‒ Good at binary and multiclass classification ‒ **Very strong assumption: conditional independence** ‒ Good with discrete features, but can be adapted for continuous features ‒ Works surprisingly well in practice.

## LDA - Linear Discriminant Analysis

‒ Generative \(can simulate data\) ‒ Good at binary and multiclass classification ‒ **Very strong assumption: Gaussian class-specific data distribution, and constant \(co\)variance.** ‒ Unclear how widely this is used these days.

[http://www.sthda.com/english/articles/36-classification-methods-essentials/146-discriminant-analysis-essentials-in-r/\#linear-discriminant-analysis---lda](http://www.sthda.com/english/articles/36-classification-methods-essentials/146-discriminant-analysis-essentials-in-r/#linear-discriminant-analysis---lda)

```text
library(MASS)
# Fit the model
model <- lda(Species~., data = train.transformed)
# Make predictions
predictions <- model %>% predict(test.transformed)
# Model accuracy
mean(predictions$class==test.transformed$Species)
```

