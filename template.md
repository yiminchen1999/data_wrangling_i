Data Import
================

I’m an R Markdown document!

# Section 1

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
    ## ✔ ggplot2 3.3.6      ✔ purrr   0.3.4 
    ## ✔ tibble  3.1.8      ✔ dplyr   1.0.10
    ## ✔ tidyr   1.2.0      ✔ stringr 1.4.1 
    ## ✔ readr   2.1.2      ✔ forcats 0.5.2 
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
getwd()
```

    ## [1] "/Users/chenyimin/Desktop/P8105 data science/data_wrangling_i"

``` r
litters_data = read_csv(file = "./data/FAS_litters.csv")
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): Group, Litter Number
    ## dbl (6): GD0 weight, GD18 weight, GD of Birth, Pups born alive, Pups dead @ ...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

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

``` r
#litters_data
tail(litters_data, 5)
```

    ## # A tibble: 5 × 8
    ##   group litter_number gd0_weight gd18_weight gd_of_birth pups_…¹ pups_…² pups_…³
    ##   <chr> <chr>              <dbl>       <dbl>       <dbl>   <dbl>   <dbl>   <dbl>
    ## 1 Low8  #100                20          39.2          20       8       0       7
    ## 2 Low8  #4/84               21.8        35.2          20       4       0       4
    ## 3 Low8  #108                25.6        47.5          20       8       0       7
    ## 4 Low8  #99                 23.5        39            20       6       0       5
    ## 5 Low8  #110                25.5        42.7          20       7       0       6
    ## # … with abbreviated variable names ¹​pups_born_alive, ²​pups_dead_birth,
    ## #   ³​pups_survive

``` r
skimr::skim(litters_data)
```

|                                                  |              |
|:-------------------------------------------------|:-------------|
| Name                                             | litters_data |
| Number of rows                                   | 49           |
| Number of columns                                | 8            |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |              |
| Column type frequency:                           |              |
| character                                        | 2            |
| numeric                                          | 6            |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |              |
| Group variables                                  | None         |

Data summary

**Variable type: character**

| skim_variable | n_missing | complete_rate | min | max | empty | n_unique | whitespace |
|:--------------|----------:|--------------:|----:|----:|------:|---------:|-----------:|
| group         |         0 |             1 |   4 |   4 |     0 |        6 |          0 |
| litter_number |         0 |             1 |   3 |  15 |     0 |       49 |          0 |

**Variable type: numeric**

| skim_variable   | n_missing | complete_rate |  mean |   sd |   p0 |   p25 |   p50 |   p75 | p100 | hist  |
|:----------------|----------:|--------------:|------:|-----:|-----:|------:|------:|------:|-----:|:------|
| gd0_weight      |        15 |          0.69 | 24.38 | 3.28 | 17.0 | 22.30 | 24.10 | 26.67 | 33.4 | ▃▇▇▆▁ |
| gd18_weight     |        17 |          0.65 | 41.52 | 4.05 | 33.4 | 38.88 | 42.25 | 43.80 | 52.7 | ▃▃▇▂▁ |
| gd_of_birth     |         0 |          1.00 | 19.65 | 0.48 | 19.0 | 19.00 | 20.00 | 20.00 | 20.0 | ▅▁▁▁▇ |
| pups_born_alive |         0 |          1.00 |  7.35 | 1.76 |  3.0 |  6.00 |  8.00 |  8.00 | 11.0 | ▁▃▂▇▁ |
| pups_dead_birth |         0 |          1.00 |  0.33 | 0.75 |  0.0 |  0.00 |  0.00 |  0.00 |  4.0 | ▇▂▁▁▁ |
| pups_survive    |         0 |          1.00 |  6.41 | 2.05 |  1.0 |  5.00 |  7.00 |  8.00 |  9.0 | ▁▃▂▇▇ |

``` r
#view(litters_data)
litters_data = read_csv(file = "./data/FAS_litters.csv",
  skip = 10, col_names = FALSE)
```

    ## Rows: 40 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): X1, X2
    ## dbl (6): X3, X4, X5, X6, X7, X8
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
head(litters_data)
```

    ## # A tibble: 6 × 8
    ##   X1    X2                 X3    X4    X5    X6    X7    X8
    ##   <chr> <chr>           <dbl> <dbl> <dbl> <dbl> <dbl> <dbl>
    ## 1 Con8  #3/5/2/2/95      28.5    NA    20     8     0     8
    ## 2 Con8  #5/4/3/83/3      28      NA    19     9     0     8
    ## 3 Con8  #1/6/2/2/95-2    NA      NA    20     7     0     6
    ## 4 Con8  #3/5/3/83/3-3-2  NA      NA    20     8     0     8
    ## 5 Con8  #2/2/95/2        NA      NA    19     5     0     4
    ## 6 Con8  #3/6/2/2/95-3    NA      NA    20     7     0     7

``` r
litters_data = read_csv(file = "./data/FAS_litters.csv",
  col_types = cols(
    Group = col_character(),
    `Litter Number` = col_character(),
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

    ## # A tibble: 6 × 8
    ##   Group `Litter Number` `GD0 weight` GD18 weig…¹ GD of…² Pups …³ Pups …⁴ Pups …⁵
    ##   <chr> <chr>                  <dbl>       <dbl>   <int>   <int>   <int>   <int>
    ## 1 Low8  #79                     25.4        43.8      19       8       0       7
    ## 2 Low8  #100                    20          39.2      20       8       0       7
    ## 3 Low8  #4/84                   21.8        35.2      20       4       0       4
    ## 4 Low8  #108                    25.6        47.5      20       8       0       7
    ## 5 Low8  #99                     23.5        39        20       6       0       5
    ## 6 Low8  #110                    25.5        42.7      20       7       0       6
    ## # … with abbreviated variable names ¹​`GD18 weight`, ²​`GD of Birth`,
    ## #   ³​`Pups born alive`, ⁴​`Pups dead @ birth`, ⁵​`Pups survive`

# Section 2
