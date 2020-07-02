# Nested grouping structure

**In certain situations, data are naturally nested in some manner. The classic example is students within classrooms within schools.**

But we can't simply use regression:

* the errors are not independent;
* want to control the group effects;
* hundreds of group indicators;

## Models

### Expression and assumptions

#### i. Regression model

$$
MATHKIND_i=b_0+b_1SES_i+\varepsilon_i
$$

#### ii. Same regression model

$$
MATHKIND_{ij}=b_0+b_1SES_{ij}+\varepsilon_{ij}
$$

ij refers to the ith student in jth school. student identifiers should be thought of as pairs \(student, school\): \(1,1\), \(2,1\), . . . , \(1,2\),\(2,2\), . . .

#### iii. Random effects

$$
MATHKIND_{ij} = b_0 + b_1SES_{ij} + \zeta_j + \varepsilon_{ij}
$$

assumptions:

$$
\zeta_j \sim N(0,\sigma_\zeta^2)
$$

$$
\varepsilon_{ij} \sim N(0,\sigma_\varepsilon^2)
$$

#### Intraclass Correlation Coefficient \(ICC\).

This is also an estimate of the correlation between subjects within schools.

$$
ICC= \frac{\sigma_\zeta^2}{\sigma_\zeta^2 + \sigma_\varepsilon^2}
$$

### Coding

The lme4 library and corresponding lmer command will primarily be used in this course.

```text
require(lme4)
lme1 <- lmer(mathkind~ses+(1|schoolid),data=dat)
print(summary(lme1))

## Random effects:
## Groups   Name        Variance Std.Dev.
## schoolid (Intercept)  309     17.58   
## Residual             1308     36.16   
## Number of obs: 1190, groups:  schoolid, 107

## Fixed effects:
##             Estimate Std. Error       df t value Pr(>|t|)    
## (Intercept)  465.746      2.058   98.752 226.337  < 2e-16 ***
## ses           10.722      1.589 1187.995   6.747 2.35e-11 ***
```

To test the nested model, test whether the random effects were necessary, whether the model gets significantly improved compared to without random effects, `rand` in`lmerTest` can be applied.

```text
require(lmerTest)
rand(lme1)


# Model:
# mathkind ~ ses + (1 | schoolid)
#                npar  logLik   AIC   LRT Df Pr(>Chisq)
# <none>            4 -6019.3 12047
# (1 | schoolid)    3 -6077.4 12161 116.1  1  < 2.2e-16 ***
```

## Simpler baseline models

i. unconditional means model \(UMM\): It documents the extent to which variation appears to be between vs. within grouping factor\(s\)

$$
MATHKIND_{ij} = b_0  + \zeta_j + \varepsilon_{ij},\mbox{ with }\zeta_j\sim N(0,\sigma_\zeta^2), \varepsilon_{ij} \sim N(0,\sigma_\varepsilon^2),\mbox{ indep.}
$$

```text
lme2 <- lmer(mathkind~(1|schoolid),data=dat)
print(summary(lme2))
rand(lme2)

# Random effects:
#  Groups   Name        Variance Std.Dev.
#  schoolid (Intercept)  364.3   19.09   
#  Residual             1344.5   36.67  
```

ICC=0.21.This suggests that if we had school-level predictors, they might ‘explain’ some of this variation. Similarly, the 79% of the variation that is within schools might be explainable via student level \(within-group\) predictors.

ii. UMM that introduces classroom level

$$
MATHKIND_{ijk} = b_0  + \eta_{jk} + \varepsilon_{ijk},\ \mbox{with}\ \eta_{jk} \sim N(0,\sigma_\eta^2)\ \mbox{and}\ \varepsilon_{ijk} \sim N(0,\sigma_\varepsilon^2);\ \mbox{with}\ \eta\perp\varepsilon
$$

\(Student i is in classroom j in school k\) actually there are still two layers.

```text
lme3 <- lmer(mathkind ~ (1 | classid), data = dat)
print(summary(lme3))
```

We see that ICC=425/\(425+1306\)=25% of the variance is between classrooms \(ignoring schools\).

Perhaps the classroom explains more variation than school? 

## Two levels of nesting - schools and classrooms

### Basic Model

$$
Y_{ijk}=b_0+\eta_{jk}+\zeta_k+\varepsilon_{ijk}
$$

* epsilon\_k suffices for schools
* eta\_jk represents the effect

assumptions: 

$$
\eta_{jk}\sim N(0,\sigma_\eta^2),\zeta_{k}\sim N(0,\sigma_\zeta^2)
$$

$$
independently\ of\ each\ other\ and\ \varepsilon_{ijk}\sim N(0,\sigma_\varepsilon^2)
$$

```text
lme4 <- lmer(mathkind ~ (1 | schoolid/classid), data = dat)
print(summary(lme4))

## Random effects:
## Groups           Name        Variance  Std.Dev.
## classid:schoolid (Intercept) 32.0      5.657
## schoolid         (Intercept) 352.8     18.784
## Residual                     1323.4    36.379
```

From the result

$$
\hat{\sigma}^2_\eta=32.0;\ \hat{\sigma}^2_\zeta=352.8
$$

So, 353/\(353+32+1323\), or about 21% of the variation is between schools, while 32/\(353+32+1323\), or 2% is between classrooms, net of schools; the remaining variation is 14 within classrooms at the student level.

### Test

```text
lm0 <- lm(mathkind ~ 1, data = dat) # linear model with same 'fixed' effects but no random effects
anova(lme4, lm0, refit = F) #test the significance of random effects (jointly).
```

Here we use `refit=F`to test both effects together. If we want to test only one random effect, for example, with both effects and with only school effect, we can omit `refit=F`. But it will automatically apply `anova` and use ML method instead of REML.

