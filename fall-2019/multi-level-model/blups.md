# BLUPs

## Predicting random effects: BLUPs

#### Basic Idea

We want to have a best guess for $$\zeta_k$$ and here is the formula. So we predict the expected $$\zeta_k$$given all the outcomes, indicators, and estimated parameters.

$$
\hat\zeta_k = E(\zeta_k\vert Y_{\cdot k},X_{\cdot k}, \hat\beta,\hat\sigma_\zeta^2,\hat\sigma_\varepsilon^2)
$$

#### How to do that

We do not give the full formula for the BLUP \(it requires matrix algebra\), but we examine several of the simpler cases. The BLUP is a **weighted average of what we might call ‘fixed effects residuals’** – the residuals we get after removing the population mean prediction.

In a model such as $$MATHGAI{N{ijk}} = {b_0} + {b_1}SE{S{ijk}} + \zeta_k + {\varepsilon{ijk}}$$, the corresponding fixed effects residual would be: $MATHGAI{N_{ijk}} - \({\hat b\_0} + {\hat b\_1}SE{S_{ijk}}\)$

