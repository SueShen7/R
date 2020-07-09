# Problems

## Categorical variable in x axis for scatterplot

![](../../../.gitbook/assets/image%20%28172%29.png)

solution: change `geom_point()` to `geom_jitter()`

## Overplotted

![](../../../.gitbook/assets/image%20%28171%29.png)

solution: adjust alpha, shape, size etc.

```text
ggplot(Vocab, aes(x=education, y=vocabulary))+
  geom_jitter(alpha = 0.2, shape = 1)
```

![](../../../.gitbook/assets/image%20%28167%29.png)

## Overlapped histogram

```text
ggplot(mtcars, aes(mpg, color = cyl)) +
  geom_freqpoly(binwidth = 1)
```

![](../../../.gitbook/assets/image%20%28175%29.png)

## Ordinal variable colors

`scale_fill_brewer`: automatically

`scale_fill_manual`: set `values` manually

```text
ggplot(Vocab, aes(x = education, fill = vocabulary)) +
  geom_bar(position = "fill") +
  scale_fill_brewer()
```

![](../../../.gitbook/assets/image%20%28168%29.png)

but it only have 9 colors, we have 11 categories, so we have to do it manually

### colorRampPalette

```text
new_col <- colorRampPalette(c("#FFFFFF", "#0000FF")) # set a function
new_col(4) # the newly extrapolated colours
munsell::plot_hex(new_col(4)) # Quick and dirty plot
```

![](../../../.gitbook/assets/image%20%28177%29.png)

```text
blues <- brewer.pal(9, "Blues")
blue_range <- colorRampPalette(blues) # set a function
ggplot(Vocab, aes(x = education, fill = vocabulary)) +
  geom_bar(position = "fill") +
  scale_fill_manual(values = blue_range(11))
```

![](../../../.gitbook/assets/image%20%28181%29.png)

## Simplify sydnax - qplot

simple but not very flexible

by default, it is geom\_point

`position`

```text
qplot(Species, Value, data = iris.tidy, col = Part,
    position = "jitter")
```

`alpha`: in the `I()` format, otherwise it will be taken as vectors

```text
qplot(Sepal.Length, Sepal.Width, data = iris, col = Species,
    position = "jitter", alpha = I(0.5))
```

`geom`

```text
qplot(Sepal.Length, Sepal.Width, data = iris, col = Species,
    geom = "jitter")
```

