# Problems

## Categorical variable in x axis for scatterplot

![](../../../.gitbook/assets/image%20%28178%29.png)

solution: change `geom_point()` to `geom_jitter()`

## Overplotted scatterplot

![](../../../.gitbook/assets/image%20%28177%29.png)

solution: adjust alpha, shape, size etc.

```text
ggplot(Vocab, aes(x=education, y=vocabulary))+
  geom_jitter(alpha = 0.2, shape = 1)
```

![](../../../.gitbook/assets/image%20%28169%29.png)

Or we can **jitter** the plot for categorical variables

## Overlapped histogram

```text
ggplot(mtcars, aes(mpg, color = cyl)) +
  geom_freqpoly(binwidth = 1)
```

![](../../../.gitbook/assets/image%20%28184%29.png)

## Ordinal variable colors

`scale_fill_brewer`: automatically

`scale_fill_manual`: set `values` manually

```text
ggplot(Vocab, aes(x = education, fill = vocabulary)) +
  geom_bar(position = "fill") +
  scale_fill_brewer()
```

![](../../../.gitbook/assets/image%20%28170%29.png)

but it only have 9 colors, we have 11 categories, so we have to do it manually

### colorRampPalette

```text
new_col <- colorRampPalette(c("#FFFFFF", "#0000FF")) # set a function
new_col(4) # the newly extrapolated colours
munsell::plot_hex(new_col(4)) # Quick and dirty plot
```

![](../../../.gitbook/assets/image%20%28186%29.png)

```text
blues <- brewer.pal(9, "Blues")
blue_range <- colorRampPalette(blues) # set a function
ggplot(Vocab, aes(x = education, fill = vocabulary)) +
  geom_bar(position = "fill") +
  scale_fill_manual(values = blue_range(11))
```

![](../../../.gitbook/assets/image%20%28190%29.png)

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

## Add something in the plot

### annotate

need to specify geom, x, y, label, vjust, size, color etc

e.g. add text

```text
plt_country_vs_lifeExp +
  step_1_themes +
  geom_vline(xintercept = global_mean, color = "grey40", linetype = 3) +
  annotate(
    "text",
    x = x_start, y = y_start,
    label = "The\nglobal\naverage",
    vjust = 1, size = 3, color = "grey40"
  )
```

e.g. add arrow \(remember to specify length and type\)

```text
plt_country_vs_lifeExp +  
  step_1_themes +
  geom_vline(xintercept = global_mean, color = "grey40", linetype = 3) +
  step_3_annotation +
  annotate(
    "curve",
    x = x_start, y = y_start,
    xend = x_end, yend = y_end,
    arrow = arrow(length = unit(0.2, "cm"), type = "closed"),
    color = "grey40"
```

