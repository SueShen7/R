# Coordinate

## scale\_

### basic scale\_functions

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
  scale_x_discrete("Cylinders", limits = c(4,8), breaks = seq(4,8,2)) + 
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

### scale\_\*\_log10

can omit limits argument and use default setting

![](../../../.gitbook/assets/image%20%28195%29.png)

### sec.axis

example: add second y axis for temperature \(2 kinds of units\)

```text
y_breaks <- c(59, 68, 77, 86, 95, 104)
y_labels <- (y_breaks - 32) * 5 / 9
secondary_y_axis <- sec_axis(
  trans = identity,
  name = "Celsius",
  breaks = y_breaks,
  labels = y_labels
)

# Update the plot
ggplot(airquality, aes(Date, Temp)) +
  geom_line() +
  # Add the secondary y-axis 
  scale_y_continuous(sec.axis = secondary_y_axis) +
  labs(x = "Date (1973)", y = "Fahrenheit")
```

![](../../../.gitbook/assets/image%20%28197%29.png)

## coord\_trans

can use any log form, but remember to adjust the labels

![](../../../.gitbook/assets/image%20%28208%29.png)

## coord\_cartesian

`xlim` or `ylim`

![](../../../.gitbook/assets/image%20%28198%29.png)

`expand = 0`: removes all buffer margin. Set the `clip` argument to `"off"` to prevent losing points on the edges.

## coord\_fixed

coord\_fixed\(\) means **units** of x and y are 1:1, it is default

![](../../../.gitbook/assets/image%20%28203%29.png)

## coord\_flip

switch x axis and y axis

could be pretty useful when draw horizontal bar charts

## labs

names of x and y axis, title, source etc

```text
labs(title = "Highest and lowest life expectancies, 2007", 
     caption = "Source: gapminder")
```

### 

