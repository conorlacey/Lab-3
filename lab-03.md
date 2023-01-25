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

There are 935 observations with 26 variables in the Nobel data set.

``` r
nobel_living<-nobel %>% 
  filter(country != is.na(country) & 
           gender != "org" &
           is.na(died_date))
```

### Exercise 2

Remove this text, and add your answer for Exercise 1 here. Add code
chunks as needed. Don’t forget to label your code chunk. Do not use
spaces in code chunk labels.

### Exercise 3

Remove this text, and add your answer for Exercise 1 here. Add code
chunks as needed. Don’t forget to label your code chunk. Do not use
spaces in code chunk labels.

### Exercise 4

…

### Exercise 5

…

### Exercise 6

…
