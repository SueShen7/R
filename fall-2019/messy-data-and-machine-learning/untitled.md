# Web Scraping

![](../../.gitbook/assets/image%20%28124%29.png)

1. `read_html()`
2. `html_nodes(x, xpath)`
3. `html_text()/html_attr()`

![](../../.gitbook/assets/image%20%28125%29.png)

```text
library(tidyverse)
library(rvest)

url <- "https://www.billboard.com/charts/year-end/2010/hot-100-artists"
response <- read_html(url)
artist_html <- html_nodes(x = response,
                          xpath = '//a[contains(@href, "music")]')
artist_html <- html_text(artist_html, trim = T)
```

#### html\_nodes: xpath

`//p[@class="class-1"]`

`//p[contains(@class,"class-1")]`

#### html\_text

```text
html_text(artist_html, trim = T)
```

#### html\_attr

```text
html_attr(artist_html, "href")
```

