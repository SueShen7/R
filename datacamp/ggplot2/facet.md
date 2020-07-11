# Facet

## facet\_grid

![](../../.gitbook/assets/image%20%28212%29.png)

example

![](../../.gitbook/assets/image%20%28218%29.png)

![](../../.gitbook/assets/image%20%28215%29.png)

### labeller

The default value is

* `label_value`: Default, displays only the value

Common alternatives are:

* `label_both`: Displays both the value and the variable name ---- `cyl 4` `cyl 6` `cyl 8`
* `label_context`: Displays only the values or both the values and variables _depending on whether multiple factors are faceted_ ---- `4` `6` `8`
* when there are two or more cols or rows, the two are the same

### scales and space

![](../../.gitbook/assets/image%20%28216%29.png)

`scales = "free_y"`

![](../../.gitbook/assets/image%20%28221%29.png)

`scales = "free_y", space = "free_y"`

![](../../.gitbook/assets/image%20%28211%29.png)

### margins

Facets are great for seeing subsets in a variable, but sometimes you want to see _both_ those subsets _and_ all values in a variable.

Here, the `margins` argument to `facet_grid()` is your friend.

* `FALSE` \(default\): no margins.
* `TRUE`: add margins to every variable being faceted by.
* `c("variable1", "variable2")`: **only add margins to the variables listed**.

![](../../.gitbook/assets/image%20%28219%29.png)

## facet\_wrap

when there are many groups and you don't want them to be on the same row or column

```text
p + facet_wrap(vars(year), ncol = ...)
#or
p + facet_wrap(~year, ncol = ...)
```

![](../../.gitbook/assets/image%20%28209%29.png)

## change labels

`fct_recode`

```text
msleep2$conservation <- fct_recode(msleep2$conservation,                   
                                   Domesticated = "domesticated",
                                   `Least concern` = "lc")
```

`factor`

```text
mtcars$fam <- factor(mtcars$am, labels = c(`0` = "automatic",
                                           `1` = "manual"))
```

## arrange order

![](../../.gitbook/assets/image%20%28214%29.png)

