# Topic 2. Hypothesis Testing

## Non parametric testing

Tests for a mean shift: `wilcox.test()` with rank

Correlations:

1.Pearson’s Correlation

_Pearson’s Correlation has three major assumptions:_

* Both X and Y are continuous. 
* X and Y are Normally distributed \(important for size and power of T test for small samples\). 
* X and Y are linearly related.
* Spearman’s Rho \(difference in rank\)

`cor.test(E, M, method = "spearman")`

### Equivalent Tests

* Is the regression coefficient in one model equivalent to the regression coefficient in another model.
* Is the difference in means between treatment 1 and treatment 2 the same \(bioequivalence\) or not.

1.Two one-sided tests \(TOST\) method

$$
H_{01} : /
$$

