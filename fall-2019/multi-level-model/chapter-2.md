# chapter 2

## Conceptualization

$$
Y_{ijk} = b_0 + b_1 X_{1ijk} + \zeta_k + \varepsilon_{ijk}, \zeta_k\sim N(0,\sigma^2_\zeta)\ independent\ of\ \varepsilon_{ijk}\sim N(0,\sigma^2_\epsilon)
$$

#### 1. random effects are part of a more complex error structure

$$
\varepsilon_{ijk}' = \zeta_k + \varepsilon_{ijk}
$$

It looks a lot like ‘plain old’ regression. But these new error terms are not independent across subjects in the same school. In other words, the random effect explains part of the variation of the observed outcome.

#### 2. effects are latent variables

The random effect in clustered level reflects a combined impact of latent variable. Some unobserved variables in school level has been counted. We can further include some specific school-level indicators to undermine the variance.

#### 3. random coefficients or intercepts

$$
{Y_{ijk}} = {b_0} + {b_1}{X_{1ijk}} + {\varepsilon '_{ijk}}
$$

It is a ‘random coefficient’ \(or random intercept\) that varies by school, not by student i in school

#### 4. separate equations for different \(nested\) levels

$$
Level\ 1: {Y_{ijk}} = {\beta_{0k}} + \beta_{1k} X_{1ijk} + {\varepsilon_{ijk}},{\varepsilon_{ijk}} \sim N(0,\sigma_\varepsilon ^2)
$$

$$
Level\ 2: {\beta_{0k}} = {b_0} + {\zeta_{0k}} ,{\beta_{1k}} = {b_1},{\zeta_{0k}}\sim N(0,\sigma_{{\zeta_0}}^2)
$$

## Model Selection

#### 1. Selecting random effects

`lmerTest::ranova`

With random effect and without

```text
lmer.fit2 <- lmer(mathgain ~ (1 | schoolid), data = dat)
ranova(lmer.fit2)

## Model:
## mathgain ~ (1 | schoolid)
##              npar   logLik    AIC     LRT Df  Pr(>Chisq)
## <none>          3  -5888.3  11783
## (1 | schoolid)  2  -5904.8  11814  32.881  1  9.796e-09***
```

With one level random effect or with two

```text
lmer.fit3 <- lmer(mathgain ~ (1 | schoolid/classid), data = dat)
anova(lmer.fit2, lmer.fit3, refit = F)

## Data: dat
## Models:
## lmer.fit2: mathgain ~ (1 | schoolid)
## lmer.fit3: mathgain ~ (1 | schoolid/classid)
##             Df   AIC   BIC  logLik deviance  Chisq Chi Df Pr(>Chisq)
## lmer.fit2    3 11783 11798 -5888.3    11777
## lmer.fit3    4 11777 11797 -5884.4    11769 7.9048   1       0.00493 **
## ---
## Signif. codes: 0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```

#### 2. Select fixed effects

Commonly, we trust REML because it is unbiased. But it is not feasible when we compare nested fixed effects. Instead, we have to use FML/ML method.

```text
lmer.fit3 <- lmer(mathgain ~ (1 | schoolid/classid), data = dat)
lmer.fit4 <- lmer(mathgain ~ ses + mathknow + (1 | schoolid/classid), data = dat)
anova(lmer.fi3, lmer.fit4, refit = F)

## refitting model(s) with ML (instead of REML)
## Data: dat
## Subset: in_sample
## Models:
## fit7: mathgain ~ 1 + (1 | schoolid/classid)
## fit8: mathgain ~ ses + mathknow + (1 | schoolid/classid)
## Df AIC BIC logLik deviance Chisq Chi Df Pr(>Chisq)
## fit7 4 10704 10724 -5347.9 10696
## fit8 6 10704 10734 -5346.1 10692 3.5921 2 0.166
```

In addition, sometimes there is error when missingness exists since LRTs are only legitimate when the included observations are the same in both models.

```text
print(try(anova(lmer.fit3, lmer.fit4, refit = F)))
## Error in anova.merMod(lmer.fit3, lmer.fit4, refit = F) :
## models were not all fitted to the same size of dataset
## [1] "Error in anova.merMod(lmer.fit3, lmer.fit4, refit = F) : 
## \n models were not all fitted to 
## attr(,"class")
## [1] "try-error"
## attr(,"condition")
## <simpleError in anova.merMod(lmer.fit3, lmer.fit4, refit = F): 
## models were not all fitted to the
```

Solution:

```text
save.options <- options() #so that old options can be restored
options(na.action = "na.pass")
mm <- model.matrix(~mathgain + ses + mathknow, data = dat)
in_sample <- apply(is.na(mm), 1, sum) == 0 # these rows aren't missing anything
options(save.options)
# re-fit mlms using only fully observed observations, even in model with
# fewer predictors.

fit7 <- lmer(mathgain ~ 1 + (1 | schoolid/classid), data = dat, subset = in_sample)
fit8 <- lmer(mathgain ~ ses + mathknow + (1 | schoolid/classid), data = dat,
subset = in_sample)
```

