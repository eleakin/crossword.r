
Generating Crosswords from Word Lists
=====================================

**Status**

<a href="https://travis-ci.org/petermeissner/crossword"> <img src="https://api.travis-ci.org/petermeissner/crossword.svg?branch=master"> <a/> <a href="https://cran.r-project.org/package=crossword"> <img src="http://www.r-pkg.org/badges/version/crossword"> </a> [![codecov](https://codecov.io/gh/petermeissner/crossword/branch/master/graph/badge.svg)](https://codecov.io/gh/petermeissner/crossword/tree/master/R) <img src="http://cranlogs.r-pkg.org/badges/grand-total/crossword"> <img src="http://cranlogs.r-pkg.org/badges/crossword">

*lines of R code:* 545, *lines of test code:* 0

**Development version**

0.3.1 - 2017-08-24 / 18:56:43

**Description**

Generate crosswords from a list of words.

**License**

MIT + file LICENSE <br>Peter Meissner

**Citation**

``` r
citation("crossword")
```

**BibTex for citing**

``` r
toBibtex(citation("crossword"))
```

**Installation**

Stable version from CRAN:

``` r
install.packages("crossword")
```

Latest development version from Github:

``` r
devtools::install_github("petermeissner/crossword")
```

Usage
=====

``` r
# load the library
library(crossword)

# create a new 4 by 4 crossword
cw <- Crossword$new(rows = 4, columns = 4)

# add a list of words
words <- c("back", "nasa", "kick", "nuk", "ic", "sic")
clues <- c("!forward", "first on moon", "... the ball", "ISO 639-3", "ISO 3166-1", "thus was it written")

cw$add_words(
  words = words,
  clues = clues
)
## #BACK# / 5 / 1 / right / 
## 
## #NASA# / 1 / 3 / down / 
## 
## #KICK# / 1 / 5 / down / 
## 
## #NUK# / 2 / 2 / right / 
## 
## #IC# / 3 / 4 / down / 
## 
## #SIC# / 4 / 2 / right /
```

``` r
# use the default print method to have a look
cw
## . 1 2 3 4 5 6
## 1 # # # # # #
## 2 # # N U K #
## 3 # . A # I #
## 4 # # S I C #
## 5 # B A C K #
## 6 # # # # # #
```

``` r
# access to letters on the grid
cw$letters
##      [,1] [,2] [,3] [,4] [,5] [,6]
## [1,] "#"  "#"  "#"  "#"  "#"  "#" 
## [2,] "#"  "#"  "N"  "U"  "K"  "#" 
## [3,] "#"  "."  "A"  "#"  "I"  "#" 
## [4,] "#"  "#"  "S"  "I"  "C"  "#" 
## [5,] "#"  "B"  "A"  "C"  "K"  "#" 
## [6,] "#"  "#"  "#"  "#"  "#"  "#"

# access to words placed on the grid, their co-ordinates and so on
cw$words
## # A tibble: 6 x 6
##     row   col length direction                clue  word
##   <int> <int>  <int>     <chr>               <chr> <chr>
## 1     5     1      4     right            !forward  BACK
## 2     1     3      4      down       first on moon  NASA
## 3     1     5      4      down        ... the ball  KICK
## 4     2     2      3     right           ISO 639-3   NUK
## 5     3     4      2      down          ISO 3166-1    IC
## 6     4     2      3     right thus was it written   SIC
```

``` r
# render to PDF
fname <- cw_to_pdf(cw)
browseURL(fname)
```
