Regular expressions
================
Patrick Barks
2019-01-15

Regular expressions (regex) provide a way to find patterns within strings of text. You can find the R help page for regular expressions using `?regex`.

[![](https://imgs.xkcd.com/comics/regular_expressions.png)](https://xkcd.com/208/)

### Finding elements that match a pattern

`grep(pattern, x)` returns the indices of the vector `x` that match the given `pattern`.

``` r
spp <- c("Polar bear",
         "Grizzly bear",
         "Cheetah",
         "Giant panda")

# find the bears
grep("bear", spp)
## [1] 1 2
```

The `grepl` function is similar, but returns logical values.

``` r
grepl("bear", spp)
## [1]  TRUE  TRUE FALSE FALSE
```

We could also tell `grep` to return the matching values rather than their indices, as in

``` r
grep("bear", spp, value = TRUE)
## [1] "Polar bear"   "Grizzly bear"
```

To match multiple search terms we can use the "or" symbol `|`, as in

``` r
grep("bear|panda", spp, value = TRUE) # match "bear" or "panda"
## [1] "Polar bear"   "Grizzly bear" "Giant panda"
```

### Case-insensitive matching

There are a number of ways to make our search case-insensitive.

``` r
spp <- c("Bear", "bear", "cheetah", "Bear")

grep("bear", spp, ignore.case = TRUE)
## [1] 1 2 4
grep("Bear|bear", spp)
## [1] 1 2 4
grep("[Bb]ear", spp)
## [1] 1 2 4
```

### Matching special characters

To match a special character within a search string, we generally need to 'escape' it with two preceding backslashes `\\`.

``` r
x0 <- c("(a)", "b", "(c)")

grep("\\(", x0) # match an opening parenthesis
## [1] 1 3
```

### Matching only at the start (^) or end ($) of a string

``` r
x1 <- c("weather_1.csv",
        "weather_2.csv",
        "weather_3.csv",
        "csvntf.txt",
        "denmark_weather_2012.csv")

grep("weather", x1)   # match "weather" anywhere
## [1] 1 2 3 5
grep("^weather", x1)  # match "weather" only at start
## [1] 1 2 3
grep("csv", x1)       # match "csv" anywhere
## [1] 1 2 3 4 5
grep("csv$", x1)      # match "csv" only at end
## [1] 1 2 3 5
```

### Wildcard matches (.)

``` r
x2 <- c("bear", "bean", "bat", "boar", "beer")

grep("b..r", x2, value = TRUE)
## [1] "bear" "boar" "beer"
```

### Matching a specified number of repeats

To match a given character a specific number of times, we can use the following expressions.

``` r
x3 <- c("ag", "acg", "accg", "acccg", "accccg")

grep("ac*g", x3, value = TRUE)     # * matches 0+ times
## [1] "ag"     "acg"    "accg"   "acccg"  "accccg"
grep("ac+g", x3, value = TRUE)     # + matches at least 1 time
## [1] "acg"    "accg"   "acccg"  "accccg"
grep("ac?g", x3, value = TRUE)     # ? matches at most 1 time
## [1] "ag"  "acg"
grep("ac{2}g", x3, value = TRUE)   # {n} matches exactly n times
## [1] "accg"
grep("ac{2,}g", x3, value = TRUE)  # {n,} matches at least n times
## [1] "accg"   "acccg"  "accccg"
grep("ac{2,3}g", x3, value = TRUE) # {n,m} matches n-m times
## [1] "accg"  "acccg"
```

Note that the repetition expressions apply to the preceding character ("c" in the examples above).

### Matching character classes

``` r
x4 <- c("1000", "one thousand", "1000.00")

grep("[[:digit:]]", x4)  # match any digit
## [1] 1 3
grep("[[:alpha:]]", x4)  # match any alphabetic character
## [1] 2
grep("[[:alnum:]]", x4)  # match any alphanumeric character
## [1] 1 2 3
grep("[[:lower:]]", x4)  # match any lowercase
## [1] 2
grep("[[:upper:]]", x4)  # match any uppercase
## integer(0)
grep("[[:space:]]", x4)  # match any space character
## [1] 2
grep("[[:punct:]]", x4)  # match any punctuation
## [1] 3
```

Note that the interpretation of character classes depends on the *locale*.

### Extracting patterns

In the examples above, we found the elements of a vector that match a given pattern. Sometimes we might want to find the specific position within each element where the pattern occurs (e.g. to extract the matching pattern).

``` r
x5 <- c("Blue: 13",
        "Red: 142",
        "5 Yellow")
```

For example, to find the position of the integers within the strings above, we could use `regexpr`, as in

``` r
rx <- regexpr("[[:digit:]]+", x5) # find patterns of repeating digits
rx
## [1] 7 6 1
## attr(,"match.length")
## [1] 2 3 1
## attr(,"index.type")
## [1] "chars"
## attr(,"useBytes")
## [1] TRUE
```

The output tells us the position and length of the matching pattern within each element. We could then extract each matching pattern using `regmatches`, as in

``` r
regmatches(x5, rx)
## [1] "13"  "142" "5"
```

### Look-ahead or look-behind

Sometimes we want to extract a specific pattern, but only if it's preceded or followed by some other pattern. We can use look-ahead `(?=...)` or look-behind `(?<=...)` expressions to do so (note that to use these we must set the argument `perl = TRUE`). Here's an example where we want to extract numbers from strings, but only if they represent a dollar value (i.e. are preceded by "$" or followed by " dollars").

``` r
x6 <- c("Car: 8000 dollars",
        "Computer: $500",
        "1 table",
        "4 chairs",
        "18 dollars cash")

# match integers followed by " dollars"
rx1 <- regexpr("[[:digit:]]+(?= dollars)", x6, perl = TRUE)
regmatches(x6, rx1)
## [1] "8000" "18"

# match integers preced by "$"
rx2 <- regexpr("[[:digit:]]+(?<=$)", x6, perl = TRUE)
regmatches(x6, rx2)
## [1] "500"
```
