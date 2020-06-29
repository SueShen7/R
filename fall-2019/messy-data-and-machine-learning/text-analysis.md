# Text Analysis

### Text preprocessing 

There are standard ways to process text to make it amenable to analyze, but often this depends on context. \[ simplify data but keep information \] :

1. Remove capitals and punctuation 
2. Stemming or lemmatizing \[ “vote”, “votes”, “voting” → “vot” vs. “better” → “good” \] 
3. Removing stop words \[ “the”, “and”, “of”, “to”, etc.\]

### Typical Processing

把段落拆散为单词

```text
library(tidytext)
plot_words <- plot_text %>% unnest_tokens(word, text)
```

统计频次

```text
plot_words <- plot_words %>% 
  group_by(story_number) %>% 
  mutate(num_words_plot=n())
```

sentiment analysis

```text
library(tidytext)
bing <- get_sentiments("bing")
```



