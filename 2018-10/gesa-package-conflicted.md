package conflicted
================
Gesa
1 October 2018

<br>

### Install `conflicted`

``` r
install.packages("conflicted")
```

<br>

### Function conflicts

``` r
library(dplyr)

filter(mtcars, cyl ==8)
```

    ##     mpg cyl  disp  hp drat    wt  qsec vs am gear carb
    ## 1  18.7   8 360.0 175 3.15 3.440 17.02  0  0    3    2
    ## 2  14.3   8 360.0 245 3.21 3.570 15.84  0  0    3    4
    ## 3  16.4   8 275.8 180 3.07 4.070 17.40  0  0    3    3
    ## 4  17.3   8 275.8 180 3.07 3.730 17.60  0  0    3    3
    ## 5  15.2   8 275.8 180 3.07 3.780 18.00  0  0    3    3
    ## 6  10.4   8 472.0 205 2.93 5.250 17.98  0  0    3    4
    ## 7  10.4   8 460.0 215 3.00 5.424 17.82  0  0    3    4
    ## 8  14.7   8 440.0 230 3.23 5.345 17.42  0  0    3    4
    ## 9  15.5   8 318.0 150 2.76 3.520 16.87  0  0    3    2
    ## 10 15.2   8 304.0 150 3.15 3.435 17.30  0  0    3    2
    ## 11 13.3   8 350.0 245 3.73 3.840 15.41  0  0    3    4
    ## 12 19.2   8 400.0 175 3.08 3.845 17.05  0  0    3    2
    ## 13 15.8   8 351.0 264 4.22 3.170 14.50  0  1    5    4
    ## 14 15.0   8 301.0 335 3.54 3.570 14.60  0  1    5    8

R will always use the last package loaded when multiple packages with the same function are available; so here it uses `dplyr::filter()` rather than `stats::filter()`

<br>

### Using `conflicted`

``` r
library(conflicted)
library(dplyr)

filter(mtcars, cyl ==8)
```

    ## Error: [conflicted] `filter` found in 2 packages.
    ## Either pick the one you want with `::` 
    ## * dplyr::filter
    ## * stats::filter
    ## Or declare a preference with `conflict_prefer()`
    ## * conflict_prefer("filter", "dplyr")
    ## * conflict_prefer("filter", "stats")

Should bring an error message, warning about `filter()` being a function in the `dplyr` and the `stats` package

<br>

### Functions in the package

``` r
conflict_prefer("filter", "dplyr")
```

    ## [conflicted] Will prefer dplyr::filter over any other package

``` r
# conflicted will prefer dplyr::filter over any other package in the future

filter(mtcars, cyl ==8)
```

    ##     mpg cyl  disp  hp drat    wt  qsec vs am gear carb
    ## 1  18.7   8 360.0 175 3.15 3.440 17.02  0  0    3    2
    ## 2  14.3   8 360.0 245 3.21 3.570 15.84  0  0    3    4
    ## 3  16.4   8 275.8 180 3.07 4.070 17.40  0  0    3    3
    ## 4  17.3   8 275.8 180 3.07 3.730 17.60  0  0    3    3
    ## 5  15.2   8 275.8 180 3.07 3.780 18.00  0  0    3    3
    ## 6  10.4   8 472.0 205 2.93 5.250 17.98  0  0    3    4
    ## 7  10.4   8 460.0 215 3.00 5.424 17.82  0  0    3    4
    ## 8  14.7   8 440.0 230 3.23 5.345 17.42  0  0    3    4
    ## 9  15.5   8 318.0 150 2.76 3.520 16.87  0  0    3    2
    ## 10 15.2   8 304.0 150 3.15 3.435 17.30  0  0    3    2
    ## 11 13.3   8 350.0 245 3.73 3.840 15.41  0  0    3    4
    ## 12 19.2   8 400.0 175 3.08 3.845 17.05  0  0    3    2
    ## 13 15.8   8 351.0 264 4.22 3.170 14.50  0  1    5    4
    ## 14 15.0   8 301.0 335 3.54 3.570 14.60  0  1    5    8

``` r
#same result as in the beginning, but you can be sure, that it is using dplyr::filter() and not stats::filter()
```

``` r
conflict_scout()
```

    ## 6 conflicts:
    ## * `filter`   : [dplyr]
    ## * `intersect`: [dplyr]
    ## * `lag`      : dplyr, stats
    ## * `setdiff`  : [dplyr]
    ## * `setequal` : [dplyr]
    ## * `union`    : [dplyr]

``` r
#shows all possible conflicts in your R session
```
