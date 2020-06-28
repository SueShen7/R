# Topic 3. Regression

## Interpretation

A one unit increase in that covariate **is associated with** an increase of in the expected value of Y, if **all other covariates are held fixed**.

_Differing coefficients by models_

How could we determine whether the two numbers are similar or siginicantly different?

When LogPPgdp and Purban are independent of each other, the two numbers are "the same".

\(So don't call X and Y independent variable and dependent variable, call them predictors/covariates and outcomes\)

## Extrapolating

![](../../.gitbook/assets/image%20%28107%29.png)

#### Residual Diagnostics and Variance Stabilizing Transformations

![](../../.gitbook/assets/image%20%2816%29.png)

## Explanation

_Example:_

_The data in this example consists of a sample of branches of a large Australian bank \(Cunningham and Heathcote, 1989\). Each branch makes transac- tions of two types, and for each of the branches we have recorded the number of transactions, T1 and T2, as well as Time, the total number of minutes of labor used by the branch in type 1 and type 2 transactions._

Fit M1 using the lm function in R and report the results of this model. Be sure to include the interpretation of the parameters, their standard errors as well as at least one measure of model adequacy. The output from the model is: 

![](../../.gitbook/assets/image%20%28110%29.png)

Interpreting the parameters, we see that for a bank that did no type 1 or type 2 transactions, we would expect that on average, a bank of that type would spend 144 minutes on these transactions. However, this estimate is not statistically signi cant from 0 which makes a lot more sense because obviously, a bank that does no type 1 or type 2 transactions will spend 0 minutes on these transactions. 

Comparing two groups of banks that have the same number of type 2 transactions but differ in that one group has exactly one more type 1 transaction than the banks in the other group, we would expect that the average amount of time spent on the these transactions would be 5.46 minutes longer for the group with the extra type 1 transaction. 

Comparing two groups of banks that have the same number of type 1 transactions but di er in that one group has exactly one more type 2 transaction than the banks in the other group, we would expect that the average amount of time spent on the these transactions would be 2.03 minutes longer for the group with the extra type 2 transaction.

Two measures of model adequacy you could report are that the R2 is 0.9091 indicating that the regression model explains 90.91% of the variability in the data. Furthermore, the p-value for the F statistic is roughly 0, indicating that the overall F test rejects the null hypothesis in favour of the alternative that the covariates in the model provide a better mean structure than an intercept alone.

## Categorical variables

Meaningless to use t-tests for multil-level categorical variables. Use F-statistic.

## Assumptions of Regression

* We have all the right covariates in the design matrix. 
* The true relationship between the covariates and the outcome is linear. 
* The errors, epsilon, are normally distributed, homoscedastic \(same variance\), have mean zero and are uncorrelated with X.

## Variable Selection

Method: Stepwise methods; Lasso

_Criteria:_ 

* For nested models, **R2** will always increase \(technically, not-decrease\) when more terms are added.
* So instead, we can use **adjusted R2**
* When comparing nested models, the **likelihood** will always increase \(technically: not decrease\) because the model will be able to fit the data more tightly.
* So instead, we can use **"Penalized likelihood methods" \(AIC, BIC\)**

_Stepwise with AIC_

```text
bigmod = lm(LBM~.-Label, data = ais)
summary(stepAIC(bigmod, scope = list(lower = ~1, upper = ~ .), direction = "both"))

summary(stepAIC(bigmod, scope = list(lower = ~1, upper = ~ .^2), direction = "both"))
```

_Lasso_

![](../../.gitbook/assets/image%20%2858%29.png)

The greater the value of lambda, the more ’s will be estimated at 0. If you set lambda too high, all your estimates will go to 0. 

The goal: Choose lambda such that the parameter estimates that yields smallest Mean Square Error. We do this through Cross-Validation.

```text
library(parcor)
mod = mylars(X, Y, k=10)
mod$coefficients
```



\*\*\*\*

