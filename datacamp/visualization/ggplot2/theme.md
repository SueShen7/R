# Theme

## Legend

### legend.position

```text
p + theme(legend.position = new_value)
```

Here, the new value can be

* `"top"`, `"bottom"`, `"left"`, or `"right'"`: place it at that side of the plot.
* `"none"`: don't draw it.
* `c(x, y)`: `c(0, 0)` means the bottom-left and `c(1, 1)` means the top-right.

### legend.key

```text
legend.key = element_rect(color = "red")
```

### legend.margin

inner margin inside the legend box

```text
legend.margin = margin(20, 30, 40, 50)
```

## Line

 line elements in the plot such as axes and gridlines have

* color
* thickness \(`size`\),
* line type \(solid line, dashed, or dotted\)

`element_line` to change linetype

`element_blank()` to remove the element

### line

all the lines

### axis.line

```text
p + theme(axis.line = element_line(color = "red", linetype = "dashed"))
```

### axis.ticks

the white boxes

![](../../../.gitbook/assets/image%20%28172%29.png)

`axis.ticks.length`

is the length of the bottom lines corresponding to x and y values

```text
axis.ticks.length = unit(2, "lines")
```

![](../../../.gitbook/assets/image%20%28165%29.png)

### panel.grid

`panel.grid.major.y`

```text
theme(panel.grid.major.y = element_line(
      # Set the color to white
      color = "white",
      # Set the size to 0.5
      size = 0.5,
      # Set the line type to dotted
      linetype = "dotted"
    ))
```

## Rect

```text
p + theme(rect = element_rect(fill = "red"))
```

### rect

all the rectangulars

### legend.key

```text
p + theme(legend.key = element_rect(color = "red"))
```

## Text

```text
p + theme(text = element_text(color = "red"))
```

### text

all the text

### axis.title

title of two axis

### axis.text

text on the two axis

### plot.title

title of the plot

### element\_text

```text
p + theme(plot.title = element_text(size=16, face="italic"))
```

## Margin

### legend.margin

inner margin inside the legend box

```text
legend.margin = margin(20, 30, 40, 50)
```

### plot.margin

```text
plot.margin = margin(10, 30, 50, 70, "mm")
```

## Special functions

### `unit`

* unit could be used to specify the thickness or length of lines, rects 
* To set a single whitespace value, use [`unit(x, unit)`](https://www.rdocumentation.org/packages/grid/topics/unit), where `x` is the amount and `unit` is the unit of measure.T
* The default unit is `"pt"` \(points\), which scales well with text. Other options include "cm", "in" \(inches\) and "lines" \(of text\).

```text
plt_mpg_vs_wt_by_cyl +
  theme(
    # Set the legend key size to 3 centimeters
    legend.key.size = unit(3,"cm")
  )
```

### `margin` 

Borders require you to set 4 positions, so use [`margin(top, right, bottom, left, unit)`](https://www.rdocumentation.org/packages/ggplot2/topics/margin)

## Save theme as objects & built in themes

```text
my_theme <- theme()
```

#### Built-in themes

```text
p1 + theme_bw()
```

"[https://ggplot2.tidyverse.org/reference/ggtheme.html](https://ggplot2.tidyverse.org/reference/ggtheme.html)"

`theme_grey()`

![](../../../.gitbook/assets/image%20%28192%29.png)

`theme_bw()`

![](../../../.gitbook/assets/image%20%28161%29.png)

`theme_linedraw()`

![](../../../.gitbook/assets/image%20%28179%29.png)

`theme_tufte()`

`theme_fivethirtyeight()`

`theme_wsj()`

