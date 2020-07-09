# Geometries

## Scatterplot

`geom_point()`, `geom_jitter()`, `geom_vline()`

essential: x, y \(in ggplot layer\)

optional: alpha, color, fill, shape, size

### geom\_point

`alpha`: translucent

```text
ggplot(diamonds, aes(x = carat, y = price, color = clarity)) +
  geom_point(alpha=0.4)
```

### add layers

the idea is that `geom_` could inherit data and `aes()` from `ggplot()`

```text
ggplot(iris, aes(x = Sepal.Length, y = Sepal.Width, col = Species)) +
    geom_point() + # inherits data and aes from ggplot()
    geom_point(data = iris.summary, shape = 15, size = 5) 
    # different data inherits aes
    # iris.summary is the summarized data, means of data
```

![](../../../.gitbook/assets/image%20%28191%29.png)

`shape`

![](../../../.gitbook/assets/image%20%28188%29.png)

in the following example, geom\_ layer inherits color from ggplot layer, but we can modify the fill given the shape

```text
ggplot(iris, aes(x = Sepal.Length, y = Sepal.Width, col = Species)) +
    geom_point() +
    geom_point(data = iris.summary, shape = 21, size = 5, fill = "#00000080")
```

![](../../../.gitbook/assets/image%20%28189%29.png)

### geom\_vline

`aes(xintercept = )`

`aes(yintercept = )`

```text
ggplot(iris, aes(x = Sepal.Length, y = Sepal.Width, col = Species)) +
    geom_point() +
    geom_vline(data = iris.summary, aes(xintercept = Sepal.Length)) +
    geom_hline(data = iris.summary, aes(yintercept = Sepal.Width))
```

![](../../../.gitbook/assets/image%20%28187%29.png)

### geom\_jitter

 The jitter geom is a convenient shortcut for [`geom_point(position = "jitter")`](https://ggplot2.tidyverse.org/reference/geom_point.html). It adds a small amount of random variation to the location of each point, and is a useful way of handling overplotting caused by discreteness in smaller datasets. \(**when x is categorical variable**\)

`width` e.g. `width = 0.1`

```text
ggplot(iris.tidy, aes(x = Species, y = Value, col = Part)) +
  geom_jitter() +
  facet_grid(. ~ Measure)
```

![](../../../.gitbook/assets/image%20%28146%29.png)

### geom\_dotplot

```text
ggplot(mtcars, aes(cyl, wt, fill = am)) +
  geom_dotplot(binaxis = "y", stackdir = "center")
  
# or

qplot(
  cyl, wt,
  data = mtcars,
  fill = am,
  geom = "dotplot",
  binaxis = "y",
  stackdir = "center"
)
```

![](../../../.gitbook/assets/image%20%28167%29.png)

### geom\_text

refer to label in aesthetics

text on plots or axes

```text
ggplot(mtcars, aes(wt, mpg, label = cyl))+
  geom_text()
```

![](../../../.gitbook/assets/image%20%28136%29.png)

`rownames(data)`

```text
ggplot(mtcars, aes(x = wt, y = mpg, label = rownames(mtcars))) +
  geom_text(color = "red")
```

![](../../../.gitbook/assets/image%20%28142%29.png)

## Bar plots

geom\_histogram\(\), geom\_bar\(\)

### geom\_histogram

**no y** is allowed in histogram

```text
ggplot(iris, aes(x = Sepal.Width)) +
    geom_histogram( )
```

`binwidth`

```text
ggplot(iris, aes(x = Sepal.Width)) +
    geom_histogram(binwidth = 0.1)
```

`..density..` count by default

```text
ggplot(iris, aes(x = Sepal.Width)) +
    geom_histogram(aes(y = ..density..), binwidth = 0.1)
```

`fill` \(in ggplot layer\)

```text
ggplot(iris, aes(x = Sepal.Width ), fill = Species) +
geom_histogram(binwidth = 0.1)
```

`position`

```text
ggplot(iris, aes(x = Sepal.Width ), fill = Species) +
    geom_histogram(binwidth = 0.1, position = "stack")
```

![](../../../.gitbook/assets/image%20%28174%29.png)

```text
ggplot(iris, aes(x = Sepal.Width ), fill = Species) +
    geom_histogram(binwidth = 0.1, position = "dodge")
```

![](../../../.gitbook/assets/image%20%28175%29.png)

```text
ggplot(iris, aes(x = Sepal.Width ), fill = Species) +
    geom_histogram(binwidth = 0.1, position = "fill")
```

![](../../../.gitbook/assets/image%20%28183%29.png)

### geom\_bar

I. no y

```text
ggplot(mtcars, aes(x = factor(cyl)) + geom_bar()
```

II. has y

```text
ggplot(iris_summ, aes(x = Species, y = avg)) +
    geom_bar(stat = "identity")
```

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

`position = "dodge"`

```text
cyl.am + geom_bar(position = "dodge") 
```

![](../../../.gitbook/assets/image%20%28158%29.png)

`position = position_dodge(width = 0.2) /..`

```text
ggplot(mtcars, aes(x = cyl, fill = am)) +
  geom_bar(position = position_dodge(width = 0.2), alpha = 0.6)
```

![](../../../.gitbook/assets/image%20%28160%29.png)



### geom\_errorbar

```text
ggplot(iris_summ, aes(x = Species, y = avg)) +
    geom_bar(stat = "identity"), fill = "grey50") +
    geom_errorbar(aes(ymin = avg - stdev, ymax = avg + stdev),
    width = 0.2)
```

![](../../../.gitbook/assets/image%20%28181%29.png)

### geom\_segment

need to specify xend, yend, size

```text
ggplot(gm2007, aes(x = lifeExp, y = country, color = lifeExp)) +
  geom_point(size = 4) +
  geom_segment(aes(xend = 30, yend = country), size = 2)
```

![](../../../.gitbook/assets/image%20%28182%29.png)

## Line plots

### geom\_line

`linetype`, `color`, `size`, among which `color` is the best, there are some fancy plots for `fill`

```text
ggplot(economics, aes(x = date, y = unemploy)) +
  geom_line()
```

draw rectangulars

```text
ggplot(economics, aes(x = date, y = unemploy/pop)) +
  geom_rect(data = recess,
         aes(xmin = begin, xmax = end, ymin = -Inf, ymax = +Inf),
         inherit.aes = FALSE, fill = "red", alpha = 0.2) +
  geom_line()
 # here recess is another dataset to add a geom layer, 
 # "begin" is the time of begining and "end" is the time of ending of recess
```

![](../../../.gitbook/assets/image%20%28163%29.png)

### geom\_smooth

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

another example

```text
ggplot(ChickWeight, aes(x = Time, y = weight, col = Diet)) +
  geom_line(aes(group = Chick), alpha=0.3) +
  geom_smooth(lwd=2, se=FALSE)
```

![](../../../.gitbook/assets/image%20%28171%29.png)

