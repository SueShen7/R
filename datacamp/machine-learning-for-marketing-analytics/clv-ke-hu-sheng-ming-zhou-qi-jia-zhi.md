# Modeling Customer Lifetime Value with Linear Regression

### Definition

CLV（Customer Lifetime Value），客户生命周期价值。CLV是对客户未来利润的有效预测，用来衡量一个客户（用户）在一段时期内 对企业有多大价值

### Application

1. 根据客户价值对客户分类，尽量获取优质客户；
2. 根据客户价值，执行推广计划，评估市场效果；
3. 制定留存策略，留住优质客户；
4. 差异化定价，针对性促销；
5. 对客户细分，提供更加针对性的服务

### Coding

1. `corrplot`

```text
library(corrplot)
salesData %>% select_if(is.numeric) %>%
  select(-id) %>% 
  cor() %>% 
  corrplot()
```

![](../../.gitbook/assets/image%20%28126%29.png)

2. Regression

3. Variance Inflation Factors - to examine the multicollinearity

 `vif` from package `rms`

```text
vif(Model1) # 1.多是比较正常的
```

4. Model Selection and prediction

To avoid overfitting, use AIC or stepwise method



