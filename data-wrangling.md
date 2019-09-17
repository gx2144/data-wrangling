data import
================
Guangling Xu
9/17/2019

## load in dataset

``` r
## reads in a dataset

litters_data = read_csv(file = "./FAS_litters.csv",
  skip = 10, col_names = FALSE)
```

    ## Parsed with column specification:
    ## cols(
    ##   X1 = col_character(),
    ##   X2 = col_character(),
    ##   X3 = col_double(),
    ##   X4 = col_double(),
    ##   X5 = col_double(),
    ##   X6 = col_double(),
    ##   X7 = col_double(),
    ##   X8 = col_double()
    ## )

``` r
litters_data
```

    ## # A tibble: 40 x 8
    ##    X1    X2                 X3    X4    X5    X6    X7    X8
    ##    <chr> <chr>           <dbl> <dbl> <dbl> <dbl> <dbl> <dbl>
    ##  1 Con8  #3/5/2/2/95      28.5  NA      20     8     0     8
    ##  2 Con8  #5/4/3/83/3      28    NA      19     9     0     8
    ##  3 Con8  #1/6/2/2/95-2    NA    NA      20     7     0     6
    ##  4 Con8  #3/5/3/83/3-3-2  NA    NA      20     8     0     8
    ##  5 Con8  #2/2/95/2        NA    NA      19     5     0     4
    ##  6 Con8  #3/6/2/2/95-3    NA    NA      20     7     0     7
    ##  7 Mod7  #59              17    33.4    19     8     0     5
    ##  8 Mod7  #103             21.4  42.1    19     9     1     9
    ##  9 Mod7  #1/82/3-2        NA    NA      19     6     0     6
    ## 10 Mod7  #3/83/3-2        NA    NA      19     8     0     8
    ## # ... with 30 more rows

``` r
litters_data = janitor::clean_names(litters_data)
names(litters_data)
```

    ## [1] "x1" "x2" "x3" "x4" "x5" "x6" "x7" "x8"

## load another dataset

``` r
pups_data = read_csv(file = "./FAS_pups.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   `Litter Number` = col_character(),
    ##   Sex = col_double(),
    ##   `PD ears` = col_double(),
    ##   `PD eyes` = col_double(),
    ##   `PD pivot` = col_double(),
    ##   `PD walk` = col_double()
    ## )

##
