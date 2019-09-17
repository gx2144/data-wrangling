data import
================
Guangling Xu
9/17/2019

## load in dataset

``` r
## reads in a dataset

litters_data = read_csv(file = "./FAS_litters.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   Group = col_character(),
    ##   `Litter Number` = col_character(),
    ##   `GD0 weight` = col_double(),
    ##   `GD18 weight` = col_double(),
    ##   `GD of Birth` = col_double(),
    ##   `Pups born alive` = col_double(),
    ##   `Pups dead @ birth` = col_double(),
    ##   `Pups survive` = col_double()
    ## )

``` r
names(litters_data)
```

    ## [1] "Group"             "Litter Number"     "GD0 weight"       
    ## [4] "GD18 weight"       "GD of Birth"       "Pups born alive"  
    ## [7] "Pups dead @ birth" "Pups survive"

``` r
litters_data = janitor::clean_names(litters_data)
names(litters_data)
```

    ## [1] "group"           "litter_number"   "gd0_weight"      "gd18_weight"    
    ## [5] "gd_of_birth"     "pups_born_alive" "pups_dead_birth" "pups_survive"

##
