# MCAR, MAR, NMAR simulation

Using vector u to determine whether missing or not.

## MCAR: u is irrelevant to y1 and y2

```text
# a) Generate missingness with a = b = 0, which corresponds to MCAR

a = 0
b = 0
# u is a variable to decide if y is missing
u = a*(y1 - 1) + b*(y2 - 5) + z3

# Compare histograms of y1 and y2 for complete cases and missing data
hist(y1[u > 0]) # random, so still normal
hist(y1[u < 0], add = TRUE, border = "red")

t.test(y1[u > 0], y1[u < 0])

# No evidence against H0 that the means are the same
# cannot confirm MCAR, its dangerous to say so
```

## MAR: u is relevant to y1, y2 \(missing value\) is relevant to u

```text
# c) Repeat for a = 2, b = 0, which corresponds to MAR

a = 2
b = 0
u = a*(y1 - 1) + b*(y2 - 5) + z3

# Compare histograms of y1 and y2 for complete cases and missing data
hist(y1[u > 0])
hist(y1[u < 0], add = TRUE, border = "red")

hist(y2[u > 0])
hist(y2[u < 0], add = TRUE, border = "red")


# Carry out a t-test for the means of y1 for complete and missing data 
t.test(y1[u > 0], y1[u < 0])

# Now we reject the hypothesis of equal means!
# Note also the estimates of mean, var and corr:
mean(y2[u > 0])
var(y2[u > 0])
cor(y1[u > 0], y2[u > 0])
```

## NMAR: u is relevant to y2, y2 is relevant to u, so whether missing or not depends on y2 itself

```text
# Repeat for a = 0, b = 2, which corresponds to NMAR

a = 0
b = 2
u = a*(y1 - 1) + b*(y2 - 5) + z3

# Compare histograms of y1 and y2 for complete cases and missing data
hist(y1[u > 0])
hist(y1[u < 0], add = TRUE, border = "red")

hist(y2[u > 0])
hist(y2[u < 0], add = TRUE, border = "red")


# Carry out a t-test for the means of y1 for complete and missing data 
t.test(y2[u > 0], y2[u < 0])

# Now we reject the hypothesis of equal means!
# Note also the estimates of mean, var and corr:
mean(y2[u > 0])
var(y2[u > 0])
cor(y1[u > 0], y2[u > 0])
```

