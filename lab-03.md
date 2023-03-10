Lab 03 - Nobel laureates
================
Conor Lacey
01/24/23

### Load packages and data

``` r
suppressWarnings(library(tidyverse))
```

``` r
nobel <- read_csv("data/nobel.csv")
```

## Exercises

### Exercise 1

There are 935 observations with 26 variables in the Nobel data set. Each
row represents an individual

### Exercise 2

``` r
nobel_living<-nobel %>% 
  filter(!is.na(country) & 
           gender != "org" &
           is.na(died_date))
```

### Exercise 3

``` r
nobel_living <- nobel_living %>%
  mutate(
    country_us = if_else(country == "USA", "USA", "Other")
  )
```

``` r
nobel_living_science <- nobel_living %>%
  filter(category %in% c("Physics", "Medicine", "Chemistry", "Economics"))
```

``` r
nobel_living_science %>% 
  ggplot(aes(y=country_us))+
  facet_wrap(~category)+
  geom_bar()+
  labs(title = "Nobel Prize Winners")+
  ylab("")
```

![](lab-03_files/figure-gfm/country_us-bar-graph-1.png)<!-- -->

It appears from the bar graphs that most nobel laureates are indeed
living in the US.

### Exercise 4

``` r
nobel_living_science <- nobel_living_science %>%
  mutate(
    born_country_us = if_else(born_country == "USA", "USA", "Other")
  )

nobel_living_science %>% count(born_country_us)
```

    ## # A tibble: 2 × 2
    ##   born_country_us     n
    ##   <chr>           <int>
    ## 1 Other             123
    ## 2 USA               105

It appears 105 of the nobel laureates were born in the US

### Exercise 5

``` r
nobel_living_science %>% 
  ggplot(aes(y=born_country_us))+
  facet_wrap(~category)+
  labs(title = "Nobel Prize Winners") +
  geom_bar()+
  ylab("")
```

![](lab-03_files/figure-gfm/born_country_us-bar-graph-1.png)<!-- -->

Aside from the economics category it appears the buzzfeed article is for
the most part true. Many of the nobel winners were born outside the US.

### Exercise 6

``` r
nobel_living_science %>%
  filter(country_us == "USA" &
           born_country_us == "Other") %>%
  count(born_country, sort = TRUE)
```

    ## # A tibble: 21 × 2
    ##    born_country       n
    ##    <chr>          <int>
    ##  1 Germany            7
    ##  2 United Kingdom     7
    ##  3 China              5
    ##  4 Canada             4
    ##  5 Japan              3
    ##  6 Australia          2
    ##  7 Israel             2
    ##  8 Norway             2
    ##  9 Austria            1
    ## 10 Finland            1
    ## # … with 11 more rows

Germany and the UK are the most common!
