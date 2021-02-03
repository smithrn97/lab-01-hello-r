Lab 01 - Hello R
================
Rebecca Smith
02/02/2021

## Load packages and data

``` r
library(tidyverse) 
library(datasauRus)
```

## Exercises

### Exercise 1

This file has 1846 rows and 3 columns. The variables incldued in the
data frame are the dataset, the x-values, and the y-values.

### Exercise 2

Below is a visualization of the dino dataset.

``` r
dino_data <- datasaurus_dozen %>%
  filter(dataset == "dino")

ggplot(data = dino_data, mapping = aes(x = x, y = y)) +
  geom_point()
```

![](lab-01-hello-r_files/figure-gfm/plot-dino-1.png)<!-- -->

The correlation between the x and y values in the dino dataset is -0.06.

``` r
dino_data %>%
  summarize(r = cor(x, y))
```

    ## # A tibble: 1 x 1
    ##         r
    ##     <dbl>
    ## 1 -0.0645

### Exercise 3

Below is the visualization for the star dataset.

``` r
star_data <- datasaurus_dozen %>%
  filter(dataset == "star")
ggplot(data = star_data, mapping = aes(x = x, y = y))+
  geom_point()
```

![](lab-01-hello-r_files/figure-gfm/plot-star-1.png)<!-- -->

The correlation for the star data, r = -0.06, is the same as the
correlation found for the dino data.

``` r
star_data %>%
  summarize(r = cor(x, y))
```

    ## # A tibble: 1 x 1
    ##         r
    ##     <dbl>
    ## 1 -0.0630

### Exercise 4

Below is a visualization of the circle data.The correlation between x
and y for the circle data is approximately -0.07. Thus, the correlation
between x and y in this dataset is slightly more negative than the star
or the dino datasets.

``` r
circle_data <- datasaurus_dozen %>%
  filter(dataset == "circle")
ggplot(data = circle_data, mapping = aes (x = x, y = y))+
  geom_point()
```

![](lab-01-hello-r_files/figure-gfm/plot-circle-1.png)<!-- -->

``` r
circle_data %>%
  summarize(r = cor(x,y))
```

    ## # A tibble: 1 x 1
    ##         r
    ##     <dbl>
    ## 1 -0.0683

### Exercise 5

Below is a visualization of all three datasets and their correlations.

``` r
ggplot(datasaurus_dozen, aes(x = x, y = y, color = dataset))+
  geom_point()+
  facet_wrap(~ dataset, ncol = 3)+
  theme(legend.position = "none")
```

![](lab-01-hello-r_files/figure-gfm/plot-all-1.png)<!-- -->

``` r
datasaurus_dozen %>%
  group_by(dataset) %>%
  summarize(r = cor(x, y)) %>%
  print(13)
```

    ## # A tibble: 13 x 2
    ##    dataset          r
    ##  * <chr>        <dbl>
    ##  1 away       -0.0641
    ##  2 bullseye   -0.0686
    ##  3 circle     -0.0683
    ##  4 dino       -0.0645
    ##  5 dots       -0.0603
    ##  6 h_lines    -0.0617
    ##  7 high_lines -0.0685
    ##  8 slant_down -0.0690
    ##  9 slant_up   -0.0686
    ## 10 star       -0.0630
    ## 11 v_lines    -0.0694
    ## 12 wide_lines -0.0666
    ## 13 x_shape    -0.0656
