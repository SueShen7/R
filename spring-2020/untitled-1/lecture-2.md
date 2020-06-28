---
description: Feb 7 2020
---

# 2. Throw away and imputation

**Methods that throw away data**

1.complete cases `mat[complete.cases(mat),]`

* inefficiency and bias
* assumption: MCAR
* special cases

2.complete variables `mat[, complete.cases(t(mat))]`

3.pairwise deletion

## **Imputation**

1.Mean imputation:

can cause big problems, particularly in skewed data or data with big pile ups e g at zero \(like income data\)

```text
mean.imp <- function (a)
  {
  missing <- is.na(a)
  a.obs <- a[!missing]
  imputed <- a
  imputed[missing] <- mean(a.obs)
  # Output the imputed vector
  return (imputed)
}

#or

mice(data.frame(d), method = "mean", m = 1, maxit = 1)
```

2.Drawing from the empirical distribution

This is better than mean imputation but still ignores relationships between variables

```text
## Simple random imputation
random.imp <- function (a)
{
  missing <- is.na(a)
  n.missing <- sum(missing)
  a.obs <- a[!missing]
  imputed <- a
  imputed[missing] <- sample (a.obs, n.missing, replace=TRUE)
  return (imputed)
}

earnings.imp <- random.imp (earning)
```

1. Last value carried forward \(LVCF\)

Requires longitudinal data, use pre-test data as post-test data

```text
for (i in 1:length(a5)) if (is.na(a5[i])) a5[i] = a5[i-1]
```

1. Next value carried backward \(NVCB\)
2. Dummy variable adjustment
3. For each predictor variable with missing data: – Plug in missing values with some arbitrary number \(0’s or the mean\) and then – include a new variable that is an indicator for missingness for the original variable with missing data

```text
# Dummy variable adjustment by inserting zeros
zero.imp <- function (a)
{
  missing <- is.na(a)
  a.obs <- a[!missing]
  imputed <- a
  imputed[missing] <- 0
  return (imputed)
}
a4 = zero.imp(Ozone)
d = is.na(Ozone)
summary(lm(Temp ~ a4 + d))
```

1. Reports from other people

## Logistic regression

```text
pi=invlogit(0.9+0.2*age)
R=rbinom(n, 1, pi)
```

