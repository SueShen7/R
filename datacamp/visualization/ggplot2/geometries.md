# Geometries

## Geometries

### geom\_point - scatterplot

```text
ggplot(mtcars, aes(x = cyl, y = mpg)) +
  geom_point()
```

![](../../../.gitbook/assets/image%20%28150%29.png)

`aes(color = )` 

`alpha`: translucent

```text
ggplot(diamonds, aes(x = carat, y = price, color = clarity)) +
  geom_point(alpha=0.4)
```

![](../../../.gitbook/assets/image%20%28147%29.png)

### geom\_smooth - add a smoothed line

```text
ggplot(diamonds, aes(x = carat, y = price))+
  geom_point() + #if you dont want those points, you can ignore this line
  geom_smooth()
```

![](../../../.gitbook/assets/image%20%28135%29.png)

`aes(color = )`

```text
ggplot(diamonds, aes(x = carat, y = price, color = clarity)) +
  geom_smooth()
```

![](../../../.gitbook/assets/image%20%28139%29.png)

`se=`

remove the error shading if `se=FALSE`

```text
dia_plot <- ggplot(diamonds, aes(x = carat, y = price))
dia_plot <- dia_plot + geom_point(alpha=0.2)
dia_plot + geom_smooth(aes(col = clarity), se = FALSE)
```

![](../../../.gitbook/assets/image%20%28154%29.png)

`method = "lm"`

```text
ggplot(mtcars, aes(x = wt, y = mpg, col = cyl)) +
  geom_point() + 
  geom_smooth(method = "lm", se=FALSE, lty = 2)
```

![](../../../.gitbook/assets/image%20%28159%29.png)

`aes(group = 1)`

```text
ggplot(mtcars, aes(x = wt, y = mpg, col = cyl)) +
  geom_point()  + 
  geom_smooth(method = "lm", se=FALSE, lty = 2) +
  geom_smooth(aes(group=1))
```

![](../../../.gitbook/assets/image%20%28137%29.png)

### geom\_jitter

 The jitter geom is a convenient shortcut for [`geom_point(position = "jitter")`](https://ggplot2.tidyverse.org/reference/geom_point.html). It adds a small amount of random variation to the location of each point, and is a useful way of handling overplotting caused by discreteness in smaller datasets. \(**when x is categorical variable**\)

```text
ggplot(iris.tidy, aes(x = Species, y = Value, col = Part)) +
  geom_jitter() +
  facet_grid(. ~ Measure)
```

![](../../../.gitbook/assets/image%20%28146%29.png)

### geom\_text

refer to label in aesthetics

### geom\_bar

`position = "stack"` by default

```text
cyl.am <- ggplot(mtcars, aes(x = factor(cyl), fill = factor(am)))
cyl.am + geom_bar(position = "stack")
```

![](../../../.gitbook/assets/image%20%28149%29.png)

`position = "fill"` , to show proportions

```text
cyl.am + geom_bar(position = "fill") 
```

![](../../../.gitbook/assets/image%20%28155%29.png)

position = "dodge"

```text
cyl.am + geom_bar(position = "dodge") 
```

![](../../../.gitbook/assets/image%20%28158%29.png)

## 

