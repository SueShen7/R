---
description: Jan 31 2020
---

# 1. Mechanisms

**Why should we care about missing data?**

* bias
* efficiency loss
* incorrect standard errors

#### Missing data mechanisms

_4 patterns:_

* Univariate nonresponse
* Multivariate nonresponse
* Monotone \(e.g. Longitude\)
* General

_converting Y to R:_  `(!is.na(Y))*1`

### _Missing Data Mechanisms \(MDMs\)_:

Rubin’s 1976 missing data theory involves two sets of parameters:

* the parameters that address the research questions \(i.e. the parameters that you would have estimated had there been no missing data\) 
* the parameters that describe the probability of missing data \(usually denoted φ

不知道 φ 也可以准确估计第一种parameter，因为只要知道产生NA的条件即可

**MCAR**

Missing Completely at Random: MCAR 

* If missing entries are due to a random computer/human error unrelated to the patients at all then we have MCAR 
* P\( R \| Y \) = R 4; R⊥Y, W1 \(R and Y are independent\) 
* For R=0 and R=1, the joint distribution of Ys and Ws should be the same

![](../../.gitbook/assets/image%20%2818%29.png)

**MAR**

Missing at Random \(MAR\) 

* If missing quality of life is a function of age and education, or treatment and health status, which we observe directly, then we have MAR 
* P\( R \| Y \) = R \| Y\_obs: Here missingness depends on observed values of the variables. 
* A simple version of this is P\( R1 \| Y1 , W \) = R1 \| W \), where W is a subset of fully observed variables in the matrix Y 
* R ⊥ Y \| W1 , W2 
* 总结一下就是，R=1和R=0时，所有的单独变量的distribution也好，joint distribution 也好，都是不一样的。只有Y \| W1 , W2，或者在这里，Y \| W2，才是相同的

![](../../.gitbook/assets/image%20%2874%29.png)

**NMAR**

* P\( R \| Y \) ≠ R \| Y\_obs 
* NMAR missingness occurs when missingness on Y \(i e R\) is caused by Y itself, by some variant of Y, or by some other variable that is related to Y, but which has not been measured 
* 所以不管怎么condition，Y的distribution一定是不同的

![](../../.gitbook/assets/image%20%2887%29.png)

_Ignorable mechanisms_

* The term ignorable reflects the fact that for these missing data mechanisms we can make inferences using our data without having to include a model for the missing data mechanism within our analysis model
* MCAR, MAR: yes;  NMAR: no

_What can we learn from simulation?_

* 永远没办法肯定MCAR，但有时可以否定MCAR
* 不容易区分MAR和NMAR



