# Text Analysis

## Common Practice

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

单词包：sentiment analysis: positive or negative; left join or inner join

```text
library(tidytext)
bing <- get_sentiments("bing")
plot_words_bing <- plot_words_all %>% inner_join(bing)
plot_words_sentiment <- plot_words_all %>% left_join(bing)
```

单词包：stopword

```text
ap_dtm <- ap_td %>% anti_join(stop_words, by = c(term = "word")) 
```

"[https://github.com/SueShen7/coursesnyu/blob/master/plot\_analysis.R](https://github.com/SueShen7/coursesnyu/blob/master/plot_analysis.R)"

## Topic Modeling

```text
# let's switch back to tidy format to get rid of stop words, then convert back
ap_td <- tidy(AssociatedPress)
ap_td %>% count(term, sort=T)

ap_dtm <- ap_td %>% anti_join(stop_words, by = c(term = "word")) 
ap_dtm %>% count(term, sort=T)

ap_dtm <- ap_dtm %>% cast_dtm(document, term, count)
ap_dtm

# fit a topic model with k = 4
ap_lda <- LDA(ap_dtm, k = 4, control = list(seed = 1234))
ap_lda

# each topic is a mixture of words; let's examine the top terms for each of the four topics
# first, examine the model (per-topic per-word probabilities)
ap_topics <- tidy(ap_lda, matrix = "beta")

ap_topics %>% filter(term=='police')
```

"[https://github.com/SueShen7/coursesnyu/blob/master/Lab%2010.R](https://github.com/SueShen7/coursesnyu/blob/master/Lab%2010.R)"

