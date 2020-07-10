# Facet

## facet\_grid

```text
plot +
  facet_grid(rows = vars(A), cols = vars(B))
```

example

![](../../../.gitbook/assets/image%20%28209%29.png)

another example

```text
ggplot(iris.tidy, aes(x = Species, y = Value, col = Part)) +
  geom_jitter() +
  facet_grid(. ~ Measure)
```

![](../../../.gitbook/assets/image%20%28145%29.png)



