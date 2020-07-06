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

Tidy data to produce the following graph

Tidy data means we have all variables all groups data in a single dataset

![](../../.gitbook/assets/image%20%28143%29.png)

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

![](../../.gitbook/assets/image%20%28144%29.png)

`aes(color = )` 

`alpha`: translucent

```text
ggplot(diamonds, aes(x = carat, y = price, color = clarity)) +
  geom_point(alpha=0.4)
```

![](../../.gitbook/assets/image%20%28142%29.png)

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

![](../../.gitbook/assets/image%20%28146%29.png)

`method = "lm"`

```text
ggplot(mtcars, aes(x = wt, y = mpg, col = cyl)) +
  geom_point() + 
  geom_smooth(method = "lm", se=FALSE, lty = 2)
```

![](../../.gitbook/assets/image%20%28147%29.png)

`aes(group = 1)`

```text
ggplot(mtcars, aes(x = wt, y = mpg, col = cyl)) +
  geom_point()  + 
  geom_smooth(method = "lm", se=FALSE, lty = 2) +
  geom_smooth(aes(group=1))
```

![](../../.gitbook/assets/image%20%28136%29.png)

