---
description: Feb 11
---

# 3. Eigenvalue decomposition, SVD

## Eigenvalue decomposition

$$
Au =\lambda u, (A-\lambda I)u=0
$$

**u** is eigenvector，λ is eigenvalue

对应不同的 λ 有不同的 **u**。

Traditionally, we store the eigenvectors of A as the columns a matrix denoted U. Eigenvalues are stored in a diagonal matrix \(denoted Λ\):

$$
AU=U\Lambda
$$

Then eigenvalue decomposition is

$$
A = U\Lambda U^{-1}
$$

And if A is symmetric, then

$$
A = U\Lambda U^{T}
$$

## Singular value decomposition

Here A is generalized to a rectangular matrix

![](../../.gitbook/assets/image%20%28114%29.png)

To summarize

$$
AA^T=P\Lambda P^T
$$

$$
A^TA=Q\Lambda Q^T
$$

虽然AAT与ATA结果不同，但这两个Λ是一样的，都是 $$\Delta$$ 的平方。

```text
svd(BrainIQ$VIQ)
svd(B)
# d is delta

eigen(BTB)
eigen(BBT)
# values are the same, showing the last 
# conclusion is correct
```

