Chile tweets
================

### Objective

To share the Twitter data used in [this]() blog post.

### Twitter

The used hashtags were:

  - **\#renunciapiñera**,
  - **\#renunciapinera** (n instead of letter ñ) and
  - **\#chiledesperto**.

The ambition was to extract 500 000 tweets created during the first week
of November, 2019. The total number of tweets downloaded ended up in
*407 976*.

``` r
## load libraries
library(rtweet)
library(tidyverse)

## Searching for 500,000 tweets containing: 
## renunciapiñera, renunciapinera or chiledesperto
rt_original <- search_tweets(
  "renunciapiñera OR renunciapinera OR chiledesperto",
  n = 500000,
  retryonratelimit = TRUE
)
```

### Download

The original file is *144 MB* large. To share the file, I used `split`
to divide the file into *four* equal parts. This is the code used for
splitting the data frame and then saving separate `.rds`.

``` r
nr_files <- 4
n <- nrow(rt_original)
split_list <- split(rt_original, rep(1:nr_files, each=ceiling(n/nr_files)))

lapply(names(split_list), function(x){
    saveRDS(split_list[x], file = paste0("rt_original_", x, ".rds"))
    })
```

**Enjoy\!**
