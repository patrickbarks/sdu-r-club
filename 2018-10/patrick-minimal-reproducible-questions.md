Getting help with an R problem on StackOverflow
================
Patrick Barks
2018-09-29

<br>

Adapted from the StackOverflow posts:

-   [How do I ask a good question?](https://stackoverflow.com/help/how-to-ask)
-   [How to create a Minimal, Complete, and Verifiable example](https://stackoverflow.com/help/mcve)

Two key components. Try to make your question

1.  minimal
2.  reproducible

<br>

##### Example question

How do I add a quadratic term to an `lme` model? Using `latency^2` in the example below gives the exact same result as without the `^2`.

``` r
# load libraries
library(nlme)
library(ggplot2)

# read data
lemna_dat_v3 <- read.csv('/Users/patrickbarks/thuRsday/BarksLairdFEcol.csv',
                         stringsAsFactors = FALSE)

# transform variable
lemna_dat_v3$parent_age <- scale(lemna_dat_v3$parent_age)

# fit lme models with or without ^2 ... results are the same!!
mod1 <- lme(lifespan ~ frond_area * chamber + curled * parent_age + latency^2,
            random = ~ 1 | ident_parent, data = lemna_dat_v3)

mod2 <- lme(lifespan ~ frond_area * chamber + curled * parent_age + latency,
            random = ~ 1 | ident_parent, data = lemna_dat_v3)
```

<br>

1. Minimal
----------

Boil the problem down to its essential components.

<br>

##### Example question (minimal)

How do I add a quadratic term to a model in R? Using `latency^2` in the example below gives the exact same result as without the `^2`.

``` r
# read data
lemna_dat_v3 <- read.csv('/Users/patrickbarks/thuRsday/BarksLairdFEcol.csv',
                         stringsAsFactors = FALSE)

# fit models with or without ^2 ... results are the same!!
mod1 <- lm(lifespan ~ latency^2, data = lemna_dat_v3)
mod2 <- lm(lifespan ~ latency, data = lemna_dat_v3)
```

<br>

2. Reproducible
---------------

Make sure your example is self-contained so that anyone with the code can reproduce the problem.

E.g. Use function `dput` to output your data to R-readable text to include in the example.

``` r
dput(lemna_dat_v3[1:5,])
```

Or, generate fake data.

``` r
dat <- data.frame(x = c(3.5, 1.7, 3.2, 1.6, 8.2, 5.1),
                  y = c(6.4, 6.2, 4.7, 1.4, 0.7, 3.2))
```

Make sure *you* can reproduce the problem in a fresh environment.

``` r
rm(list=ls()) # clear objects in workspace
# but doesn't unload packages...
# good practice to completely restart R and re-verify your example code
```

<br>

##### Example question (minimal and reproducible)

How do I add a quadratic term to a model in R? Using `x^2` in the example below gives the exact same result as without the `^2`.

``` r
dat <- data.frame(x = c(3.5, 1.7, 3.2, 1.6, 8.2, 5.1),
                  y = c(6.4, 6.2, 4.7, 1.4, 0.7, 3.2))

mod1 <- lm(y ~ x^2, data = dat)
mod2 <- lm(y ~ x, data = dat)
```
