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

```text
posn.j <- position_jitter(0.1)
ggplot(data, aes())+
    geom_point(position = posn.j)
```

### scale\_

modify x axis y axis legends

_specific functions:_

* `scale_x_discrete` 
* `scale_y_continuous`
* `scale_fill_manual`
* ...

_commands in functions:_

* `limits`
* `breaks`
* `expand`
* `labels`
* ...

```text
val = c("#E41A1C", "#377EB8")
lab = c("Manual", "Automatic")
cyl.am +
  geom_bar(position = "dodge") +
  scale_x_discrete("Cylinders") + 
  scale_y_continuous("Number") +
  scale_fill_manual("Transmission", values = val, labels = lab) 
  ## here the first argument is the name of the legend, values and labels modifies
  ## colors and names of labels
```

![](../../../.gitbook/assets/image%20%28138%29.png)

```text
ggplot(mtcars, aes(x = mpg, y = 0)) + ## here we only have x, we dont have y
  geom_jitter()+ ## but with the help of jitter, we can visualize the x
  scale_y_continuous(limits = c(-2,2))
```

![](../../../.gitbook/assets/image%20%28156%29.png)

### labs

names of x and y axis, title, source etc

```text
labs(title = "Highest and lowest life expectancies, 2007", 
     caption = "Source: gapminder")
```

### group

group the data but provide no color difference

```text
ggplot(ChickWeight, aes(x = Time, y = weight)) +
  geom_line(aes(group = Chick))
```

![](../../../.gitbook/assets/image%20%28176%29.png)







