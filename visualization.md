# Visualization

`plot` in R

```text
plot(x = BGS$HT2, y = BGS$HT9, 
     col = as.factor(BGS$Sex),
     xlab = "heights at age 2",
     ylab = "heights at age 9")
legend("topleft", c("boy","girl"), 
     col=c("black","red"), pch = 1)
```

![](.gitbook/assets/image%20%28104%29.png)

* `legend` : position, col, pch \(point type\), lty \(line type\)

![](.gitbook/assets/image%20%28109%29.png)

![](.gitbook/assets/image%20%2817%29.png)



