First R Markdown
================
Zachary Katz
2021-09-16

I’m an R Markdown document!

# Section 1

Here’s a **code chunk** that samples from a *normal distribution*:

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──

    ## ✓ ggplot2 3.3.5     ✓ purrr   0.3.4
    ## ✓ tibble  3.1.4     ✓ dplyr   1.0.7
    ## ✓ tidyr   1.1.3     ✓ stringr 1.4.0
    ## ✓ readr   2.0.1     ✓ forcats 0.5.1

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
samp=rnorm(500)
```

# Section 2

I can take the mean of the sample, too! The mean is 0.0588608.

# Section 3

Let’s write a new code chunk.

This code chunk imports the `tidyverse`, creates a data frame, and makes
a histogram.

``` r
set.seed(1234)

plot_df <- 
      tibble(
            x = rnorm(1000, sd = .5),
            y = 1 + 2 * x + rnorm(1000)
      )
plot_df
```

    ## # A tibble: 1,000 × 2
    ##         x      y
    ##     <dbl>  <dbl>
    ##  1 -0.604 -1.41 
    ##  2  0.139  1.58 
    ##  3  0.542  0.545
    ##  4 -1.17  -0.710
    ##  5  0.215  2.13 
    ##  6  0.253 -0.400
    ##  7 -0.287  1.36 
    ##  8 -0.273  0.229
    ##  9 -0.282 -0.238
    ## 10 -0.445  0.556
    ## # … with 990 more rows

``` r
ggplot(plot_df, aes(x=x)) + geom_histogram()
```

![](first_rmd_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

## Learning Assessment

This is the learning assessment from the course website. Instructions
are as follows: *Write a named code chunk that creates a dataframe
comprised of: a numeric variable containing a random sample of size 500
from a normal variable with mean 1; a logical vector indicating whether
each sampled value is greater than zero; and a numeric vector containing
the absolute value of each element. Then, produce a histogram of the
absolute value variable just created. Add an inline summary giving the
median value rounded to two decimal places. What happens if you set eval
= FALSE to the code chunk? What about echo = FALSE?/*

``` r
set.seed(12)
learning_assessment_df <- 
      tibble(
            x = rnorm(500, mean = 1),
            y = x > 0,
            abs_x = abs(x)
      )

ggplot(learning_assessment_df, aes(x=abs_x)) + geom_histogram()
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](first_rmd_files/figure-gfm/learning_assessment-1.png)<!-- -->

``` r
median_samp = median(pull(learning_assessment_df, abs_x))
```

The median of the variable containing absolute values is 1.02.

-   Also, this is a practice bullet point.
