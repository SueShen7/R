---
description: explore and explain
---

# ggplot2

## Introduction

### 7 layers

![](../../.gitbook/assets/image%20%28139%29.png)

### Grammar

We can write as

```text
ggplot(diamonds, aes(x = carat, y = price, color = clarity)) +
  geom_point(alpha=0.4)
```

or

```text
dia_plot <- ggplot(diamonds, aes(x = carat, y = price))
dia_plot + geom_point(aes(color = clarity), alpha=0.4)
```

### Data structure

**Wide and tidy**

![](../../.gitbook/assets/image%20%28150%29.png)

 The `gather()` function moves information from the columns to the rows. It takes multiple columns and _gathers_ them into a single column by adding rows. Remember to "remove" all categorical variables with "-“ \(making them unchanged\).

The `separate()` function splits one column into two or more columns according to a pattern you define. c\(\) includes the two variable names in the new dataset, " " includes the symbol that could seperate the corresponding variable.

The `spread()` function spread a key-value pair across multiple columns. It converts a multi level categorical variable to several columns.

To produce tidy data:

```text
iris.tidy <- iris %>%
  gather(key, Value, -Species) %>%
  separate(key, c("Part", "Measure"), "\\.")
```

To produce wide data \(one more step with tidy data\):

```text
iris.wide <- iris %>%
  gather(key, value, -Species) %>%
  separate(key, c("Part", "Measure"), "\\.") %>%
  spread(Measure, value)
```

Produced with tidy data:

![](../../.gitbook/assets/image%20%28145%29.png)

Produced with wide data: **\(more reasonable\)**

```text
ggplot(iris.wide, aes(x=Length, y=Width, color = Part))+
  geom_jitter()+
  facet_grid(.~Species)
```

![](../../.gitbook/assets/image%20%28147%29.png)

## Aesthetics

refers to `aes()`

### color

both **continous and categorical** variable are fine. if color depends on a continous variable, it will give a continous color

```text
ggplot(mtcars, aes(x = wt, y = mpg, color = disp)) +
  geom_point()
```

![](../../.gitbook/assets/image%20%28138%29.png)

### size

the size must be a **continous** scale

```text
ggplot(mtcars, aes(x = wt, y = mpg, size = disp)) +
  geom_point()
```

![](../../.gitbook/assets/image%20%28140%29.png)

### shape

shape requires a **categorical** variable

## Geometries

### geom\_point - scatterplot

```text
ggplot(mtcars, aes(x = cyl, y = mpg)) +
  geom_point()
```

![](../../.gitbook/assets/image%20%28146%29.png)

`aes(color = )` 

`alpha`: translucent

```text
ggplot(diamonds, aes(x = carat, y = price, color = clarity)) +
  geom_point(alpha=0.4)
```

![](../../.gitbook/assets/image%20%28144%29.png)

### geom\_smooth - add a smoothed line

```text
ggplot(diamonds, aes(x = carat, y = price))+
  geom_point() + #if you dont want those points, you can ignore this line
  geom_smooth()
```

![](../../.gitbook/assets/image%20%28135%29.png)

`aes(color = )`

```text
ggplot(diamonds, aes(x = carat, y = price, color = clarity)) +
  geom_smooth()
```

![](../../.gitbook/assets/image%20%28137%29.png)

`se=`

remove the error shading if `se=FALSE`

```text
dia_plot <- ggplot(diamonds, aes(x = carat, y = price))
dia_plot <- dia_plot + geom_point(alpha=0.2)
dia_plot + geom_smooth(aes(col = clarity), se = FALSE)
```

![](../../.gitbook/assets/image%20%28149%29.png)

`method = "lm"`

```text
ggplot(mtcars, aes(x = wt, y = mpg, col = cyl)) +
  geom_point() + 
  geom_smooth(method = "lm", se=FALSE, lty = 2)
```

![](../../.gitbook/assets/image%20%28151%29.png)

`aes(group = 1)`

```text
ggplot(mtcars, aes(x = wt, y = mpg, col = cyl)) +
  geom_point()  + 
  geom_smooth(method = "lm", se=FALSE, lty = 2) +
  geom_smooth(aes(group=1))
```

![](../../.gitbook/assets/image%20%28136%29.png)

### geom\_jitter

 The jitter geom is a convenient shortcut for [`geom_point(position = "jitter")`](https://ggplot2.tidyverse.org/reference/geom_point.html). It adds a small amount of random variation to the location of each point, and is a useful way of handling overplotting caused by discreteness in smaller datasets. \(**when x is categorical variable**\)

```text
ggplot(iris.tidy, aes(x = Species, y = Value, col = Part)) +
  geom_jitter() +
  facet_grid(. ~ Measure)
```

![](../../.gitbook/assets/image%20%28143%29.png)



## Facet

### facet\_grid

```text
ggplot(iris.tidy, aes(x = Species, y = Value, col = Part)) +
  geom_jitter() +
  facet_grid(. ~ Measure)
```

![](../../.gitbook/assets/image%20%28142%29.png)

