# Tree-Based Methods

## Decision trees for classification

### Definition

![](../../.gitbook/assets/image%20%28132%29.png)

In the classification context, there are three common ways to measure the “impurity” of a node. 

* Classification error rate: min\(p, 1-p\) 
* Gini index: 2p\(1-p\) 
* Cross-entropy/deviance: -plog\(p\) - \(1-p\)\*log\(1-p\)

\(Complex algorithm omitted.\)

### Advantages & Disadvantages

Advantages: 

* Easy to explain and interpret 
* Quick to fit and to make predictions
* Can be used for classification and regression 
* Can handle qualitative/quantitative predictors and missing data 

Disadvantages: 

* Predictive performance is not always optimal \[ easy to overfit \] 
* **Tends to be a high variance learning method \[ a different training set can give a very different tree \]**

## Bagging and boosting

![](../../.gitbook/assets/image%20%28131%29.png)

### Bootstrap Aggregation \[ Bagging Trees \]

We can create many bootstrapped versions of our dataset, fit a decision tree on each one, and combine the results. \[ recall: bootstrapping means sampling with replacement \]

How should we combine the results? – To generate a _binary prediction_, we could have each tree “vote,” then take the majority vote – To generate a _probability estimate_, we could take the proportion from the relevant leaf from each tree, then average these proportions.

#### Advantage:

* Reduce variance of models since there are lots of training sets
* Can be considered as a "natural cross validation" since in each bootstrapped training data set, about 33% of the points in the original training data will not appear. So we can make predictions based on the remaining points, repeat and measure the model performance.

### Random Forest

The fundamental difference between bagging and random forest is that in Random forests, **only a subset of features are selected at random** out of the total and the best split feature from the subset is used to split each node in a tree, unlike in bagging where all features are considered for splitting a node

#### Feature Importance

* For a feature, sum the decrease in Gini index over all splits in all trees where that feature was used. 
* For a feature, permute its values in the out-of-bag samples that are passed down each tree, then compute the average decrease in accuracy across all trees

#### Code

```text
training_set <- training_set %>% 
  filter(is.na(month)==FALSE,
         is.na(weekday)==FALSE)

model2 <- ranger(
  formula         = outcome ~ cuisine+borough+month+weekday+
    num_previous_low_inspections+num_previous_med_inspections+
    num_previous_high_inspections+num_previous_closings, 
  data            = training_set, 
  num.trees       = 1000,
  respect.unordered.factors = TRUE
)
predicted_prob = predict(model2, testing_set, type = 'response')$predictions
perf <- prediction(predicted_prob, testing_set$outcome)
auc <- performance(perf, "auc")
auc <- auc@y.values[[1]]
auc
```

