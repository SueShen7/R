# BLUPs

## Predicting random effects: BLUPs

#### Basic Idea

We want to have a best guess for $$\zeta_k$$ and here is the formula. So we predict the expected $$\zeta_k$$given all the outcomes, indicators, and estimated parameters.

$$
\hat\zeta_k = E(\zeta_k\vert Y_{\cdot k},X_{\cdot k}, \hat\beta,\hat\sigma_\zeta^2,\hat\sigma_\varepsilon^2)
$$

### How to do that \(optional\)?

We do not give the full formula for the BLUP \(it requires matrix algebra\), but we examine several of the simpler cases. The BLUP is a **weighted average of what we might call ‘fixed effects residuals’** – the residuals we get after removing the population mean prediction.

i. In a model such as $$MATHGAI{N{ijk}} = {b_0} + {b_1}SE{S{ijk}} + \zeta_k + {\varepsilon_{ijk}}$$, the corresponding fixed effects residual would be: $$MATHGAI{N{ijk}} - ({\hat b_0} + {\hat b_1}SE{S{ijk}})$$. 

ii. Then we calculate a weighted average: combines only the relevant observations: those that are in the same school, in our example. Now we get $$\hat{e}_{.k}=\sum\limits_{i,j} (Y_{ijk} - X_{ijk}\hat\beta).$$

iii. Calculate the expected $$\zeta_k$$based on the following formula. 

When $$n_k=1$$, the right side $$=ICC\hat{e}_{.k}$$

$$
\hat \zeta_k\vert \hat e_{\cdot k},\hat\sigma_\zeta^2,\hat \sigma_\varepsilon^2 = \frac{\hat\sigma_\zeta^2}{\hat\sigma_\varepsilon^2 + n_k\hat\sigma_\zeta^2}\hat e_{\cdot k}
$$

### Code

```text
    fit2 <- lmer(mathgain~1+(1|schoolid/classid),data=dat)
    print(summary(fit2))
    #generate BLUPs for random effs
    ranefs <- ranef(fit2)
    zetaM3 <- ranefs$schoolid[,1]
    etaM3 <- ranefs$classid[,1]
```

### What for

i. examine the BLUPs themselves to see does it fit the assumptions through density plot and q-q plot

```text
    plot(density(zetaM3))
    qqnorm(zetaM3);qqline(zetaM3)
    plot(density(etaM3))
    qqnorm(etaM3);qqline(etaM3)
```

ii. make predictions for new data

## Residual plot and longitudinal data

### Residual plot for assumptions

In addition to the above assumption examination based on BLUPs, we can also check the assumptions for $$\epsilon$$

```text
# *now residuals predict resM3, residual
resM3 <- residuals(fit2) #this has both school & classrm effects taken out
# kdensity resM3
plot(density(resM3))
qqnorm(resM3)
qqline(resM3)
```

### Examining residuals to uncover non-linearity

Use boxplot or smoothed line to uncover non-linearity: a linear trend might be considered

```text
ggplot(dat, aes(x = icoso, y = resMconst)) + geom_boxplot()
```

![](../../.gitbook/assets/image%20%28134%29.png)

```text
ggplot(data = dat[bool, ], aes(y = resMconst, x = yearstea)) + geom_point() +
stat_smooth(method = "loess", span = 0.3, col = 2) + geom_smooth(col = 3,
se = F)
```

![](../../.gitbook/assets/image%20%28133%29.png)

Then pay attention to polynomial trends, autocorrelation, heteroscedasticity in residual plots.

## Information criteria

```text
anova(fit.Mconst, fit.Mlin, fit.Mcubic, fit.MearlyLin, fit.MearlyQuad, refit = F)
# Data: dat
# Models:
# fit.Mconst: mathgain ~ 1 + (1 | schoolid)
# fit.Mlin: mathgain ~ yearstea + (1 | schoolid)
# fit.MearlyLin: mathgain ~ yt_early + yt_late + (1 | schoolid)
# fit.Mcubic: mathgain ~ yearstea + I(yearstea^2) + I(yearstea^3) + (1 | schoolid)
# fit.MearlyQuad: mathgain ~ yt_early + I(yt_early^2) + yt_late + (1 | schoolid)
#                npar   AIC   BIC  logLik deviance  Chisq Df Pr(>Chisq)    
# fit.Mconst        3 11785 11800 -5889.6    11779                         
# fit.Mlin          4 11787 11807 -5889.3    11779 0.6833  1     0.4084    
# fit.MearlyLin     5 11787 11813 -5888.7    11777 1.2260  1     0.2682    
# fit.Mcubic        6 11789 11820 -5888.7    11777 0.0218  1     0.8826    
# fit.MearlyQuad    6 11782 11812 -5885.0    11770 7.3142  0     <2e-16 ***
# ---
# Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
```

