# Model Evaluation

## Model Evaluation

### Accuracy

number of correct predictions/ total predictions

### Precision

actually and predicted true/ predicted true

```text
cat('At the threshold of', threshold, 'the precision is',
    nrow(filter(test, prediction==T, found.weapon==T))/
    nrow(filter(test, prediction==T)))
```

### Recall

actually true and predicted true/ actually true

```text
cat('At the threshold of', threshold, 
    ' and the recall is ',
    nrow(filter(test, prediction==T, found.weapon==T))/
    nrow(filter(test, found.weapon==T)))
```

### AUC

ROC: we could plot the true positive rate \(TPR\) vs. false positive rate \(FPR\) for all possible thresholds. This is the ROC curve.

![](../../.gitbook/assets/image%20%28118%29.png)

AUC: “Area Under \(ROC\) Curve”

```text
model <- glm(formula, data = sqf_pre_train, family = 'binomial')
sqf_2015 <- sqf_2015 %>% mutate(predicted.probability =  
                          predict(model, sqf_2015, type='response'))

# calculate AUC
test.pred <- prediction(test$predicted.probability, test$found.weapon)
test.perf <- performance(test.pred, "auc")
cat('the auc score is ', test.perf@y.values[[1]], "\n")
```

### Visualization

![](../../.gitbook/assets/image%20%28119%29.png)

```text
# SLIDE 43
# make performance plot (uncomment code)
 plot.data <- test %>% arrange( desc(predicted.probability) ) %>%
   mutate(numstops = row_number(), percent.outcome = cumsum( found.weapon )/sum( found.weapon ),
          stops = numstops/n()) %>% select(stops, percent.outcome)

 theme_set(theme_bw())
 p <- ggplot(data=plot.data, aes(x=stops, y=percent.outcome))
 p <- p + geom_line()
 p <- p + scale_x_log10('\nPercent of stops', limits=c(0.003, 1), breaks=c(.003,.01,.03,.1,.3,1),
                        labels=c('0.3%','1%','3%','10%','30%','100%'))
 p <- p + scale_y_continuous("Percent of weapons recovered", limits=c(0, 1), labels=scales::percent)
 p
 #ggsave(plot=p, file='performance_plot.png', height=5, width=5)
```

## Two goals

1. Model selection
2. Model assessment

### Simplist option

![](../../.gitbook/assets/image%20%28123%29.png)

### K-fold cross-validation

![](../../.gitbook/assets/image%20%28122%29.png)

Generally we use k=5 or k=10

```text
library(tidyverse)
library(caret)

# Define training control
set.seed(123) 
train.control <- trainControl(method = "cv", number = 10)
# Train the model
model <- train(Fertility ~., data = swiss, method = "lm",
               trControl = train.control)
# Summarize the results
print(model)
```

"[http://www.sthda.com/english/articles/38-regression-model-validation/157-cross-validation-essentials-in-r/](http://www.sthda.com/english/articles/38-regression-model-validation/157-cross-validation-essentials-in-r/)"

## Bootstrap

The bootstrap works as follows: generate many new datasets by **sampling from your original dataset with replacement**. Estimate your quantity of interest on each “bootstrapped” dataset, then see how these estimates vary.

"[https://github.com/SueShen7/coursesnyu/blob/master/Lab 7 - the bootstrap.R](https://github.com/SueShen7/coursesnyu/blob/master/Lab%207%20-%20the%20bootstrap.R)"

