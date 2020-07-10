# Introduction

## Introduction

### 7 layers

![](../../../.gitbook/assets/image%20%28141%29.png)

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

![](../../../.gitbook/assets/image%20%28157%29.png)

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

![](../../../.gitbook/assets/image%20%28148%29.png)

Produced with wide data: **\(more reasonable\)**

```text
ggplot(iris.wide, aes(x=Length, y=Width, color = Part))+
  geom_jitter()+
  facet_grid(.~Species)
```

![](../../../.gitbook/assets/image%20%28151%29.png)



