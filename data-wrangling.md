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

## Parsing columns

``` r
litters_data = read_csv(file = "./FAS_litters.csv",
  col_types = cols(
    Group = col_character(),
    `Litter Number` = col_character(), ##`means space
    `GD0 weight` = col_double(),
    `GD18 weight` = col_double(),
    `GD of Birth` = col_integer(),
    `Pups born alive` = col_integer(),
    `Pups dead @ birth` = col_integer(),
    `Pups survive` = col_integer()
  )
)
tail(litters_data)
```

    ## # A tibble: 6 x 8
    ##   Group `Litter Number` `GD0 weight` `GD18 weight` `GD of Birth`
    ##   <chr> <chr>                  <dbl>         <dbl>         <int>
    ## 1 Low8  #79                     25.4          43.8            19
    ## 2 Low8  #100                    20            39.2            20
    ## 3 Low8  #4/84                   21.8          35.2            20
    ## 4 Low8  #108                    25.6          47.5            20
    ## 5 Low8  #99                     23.5          39              20
    ## 6 Low8  #110                    25.5          42.7            20
    ## # ... with 3 more variables: `Pups born alive` <int>, `Pups dead @
    ## #   birth` <int>, `Pups survive` <int>

## Read in an excel

``` r
library(readxl)
mlb11_data = read_excel("./mlb11.xlsx", n_max = 20)
head(mlb11_data, 5)
```

    ## # A tibble: 5 x 12
    ##   team   runs at_bats  hits homeruns bat_avg strikeouts stolen_bases  wins
    ##   <chr> <dbl>   <dbl> <dbl>    <dbl>   <dbl>      <dbl>        <dbl> <dbl>
    ## 1 Texa~   855    5659  1599      210   0.283        930          143    96
    ## 2 Bost~   875    5710  1600      203   0.28        1108          102    90
    ## 3 Detr~   787    5563  1540      169   0.277       1143           49    95
    ## 4 Kans~   730    5672  1560      129   0.275       1006          153    71
    ## 5 St. ~   762    5532  1513      162   0.273        978           57    90
    ## # ... with 3 more variables: new_onbase <dbl>, new_slug <dbl>,
    ## #   new_obs <dbl>

## load haven

``` r
library(haven)
pulse_data = read_sas("./public_pulse_data.sas7bdat")
head(pulse_data, 5)
```

    ## # A tibble: 5 x 7
    ##      ID   age Sex   BDIScore_BL BDIScore_01m BDIScore_06m BDIScore_12m
    ##   <dbl> <dbl> <chr>       <dbl>        <dbl>        <dbl>        <dbl>
    ## 1 10003  48.0 male            7            1            2            0
    ## 2 10015  72.5 male            6           NA           NA           NA
    ## 3 10022  58.5 male           14            3            8           NA
    ## 4 10026  72.7 male           20            6           18           16
    ## 5 10035  60.4 male            4            0            1            2

``` r
skimr::skim(pulse_data)
```

    ## Skim summary statistics
    ##  n obs: 1087 
    ##  n variables: 7 
    ## 
    ## -- Variable type:character ----------------------------------------------------------------------------------------------
    ##  variable missing complete    n min max empty n_unique
    ##       Sex       0     1087 1087   4   6     0        2
    ## 
    ## -- Variable type:numeric ------------------------------------------------------------------------------------------------
    ##      variable missing complete    n     mean      sd        p0      p25
    ##           age       0     1087 1087    63.87   11.59    25.82     55.96
    ##  BDIScore_01m     258      829 1087     6.05    6.76     0         1   
    ##  BDIScore_06m     388      699 1087     5.67    6.46     0         1   
    ##  BDIScore_12m     233      854 1087     6.1     7.03    -0.014     1   
    ##   BDIScore_BL       0     1087 1087     7.99    6.92     0         3   
    ##            ID       0     1087 1087 14827.64 2870.61 10003     12302.5 
    ##       p50      p75    p100     hist
    ##     63.83    71.72    95.8 <U+2581><U+2581><U+2583><U+2586><U+2587><U+2585><U+2582><U+2581>
    ##      4        9       48   <U+2587><U+2582><U+2581><U+2581><U+2581><U+2581><U+2581><U+2581>
    ##      4        8       49   <U+2587><U+2582><U+2581><U+2581><U+2581><U+2581><U+2581><U+2581>
    ##      4        9       49   <U+2587><U+2582><U+2581><U+2581><U+2581><U+2581><U+2581><U+2581>
    ##      6       11       48   <U+2587><U+2585><U+2582><U+2581><U+2581><U+2581><U+2581><U+2581>
    ##  14755    17234    19983   <U+2587><U+2587><U+2587><U+2587><U+2587><U+2587><U+2586><U+2586>
