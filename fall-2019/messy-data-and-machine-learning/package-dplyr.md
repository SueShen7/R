# Basic Functions

`library(dplyr)` or `library(tidyverse)`

1. `filter()`
2. `select()`
3. `mutate()`
4. `arrange()`
5. `summarise()`
6. `group_by()`

### Additional functions

`slice`

```text
training_tweets <- tweets %>% slice(1:split_size)
testing_tweets <- tweets %>% slice((split_size+1:nrow(tweets)))
```

Create train and test

```text
library(caret)
set.seed(7267166)
trainIndex=createDataPartition(mydata$prog, p=0.7)$Resample1
train=mydata[trainIndex, ]
test=mydata[-trainIndex, ]
```

`case_when`

```text
test <- test %>% mutate(prediction = case_when(
  predicted.probability < threshold ~ F,
  predicted.probability >= threshold ~ T
))
```

`ggarrange`

```text
ggarrange(p1,p2,nrow=1,ncol=2)
```

`ggsave`

```text
p <- ggplot(hour_count2, aes(x=hour, y=count, color = crime)) +
  geom_line()
ggsave("question_a3_2.png", path = 'hw4_Liang_Shen/figures',
       width = 20, height = 10, unit = "cm")
```

`write_csv`

```text
write_csv(coefficients,path='hw3_Gao_Feng_Shen/data/question_a2_coefficients.csv')
```



