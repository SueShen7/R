# Aesthetics

## Aesthetics

refers to `aes()`

```text
ggplot(mtcars, aes(x = wt, y = mpg, fill = cyl)) +
  geom_point(shape = 21, size = 4, alpha = 0.6) 
## specific parameters should be written in geom layer
```

![](../../../.gitbook/assets/image%20%28153%29.png)

### color

color is the outside layer of a shape

both **continous and categorical** variable are fine. if color depends on a continous variable, it will give a continous color

```text
ggplot(mtcars, aes(x = wt, y = mpg, color = disp)) +
  geom_point()
```

![](../../../.gitbook/assets/image%20%28140%29.png)

more options in color could refer to scale\_ in [Coordinate](coordinate.md#scale_color_brewer).

### size

the size must be a **continous** scale

```text
ggplot(mtcars, aes(x = wt, y = mpg, size = disp)) +
  geom_point()
```

![](../../../.gitbook/assets/image%20%28143%29.png)

### shape

shape requires a **categorical** variable

### fill

fill color

### alpha

transparency 0 is transparent

### linetype

line dash pattern

### label

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

### position

modify position of points, or bars

e.g. `position = "jitter"/"dodge"/"fill"/"stack"`

or if we want to specify width

e.g. `posn <- position_jitter(0.1) /  position_dodge(0.1) /` 

`position_jitterdodge(jitter.width = 0.2, dodge.width = 0.1)`

```text
posn.j <- position_jitter(0.1)
ggplot(data, aes())+
    geom_point(position = posn.j)
```

`jitter_dodge` in `geom_point()`:

![](../../../.gitbook/assets/image%20%28204%29.png)

### 

### group

group the data but provide no color difference

```text
ggplot(ChickWeight, aes(x = Time, y = weight)) +
  geom_line(aes(group = Chick))
```

![](../../../.gitbook/assets/image%20%28176%29.png)







