Data tidy
================

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──

    ## ✓ ggplot2 3.3.5     ✓ purrr   0.3.4
    ## ✓ tibble  3.1.2     ✓ dplyr   1.0.7
    ## ✓ tidyr   1.1.3     ✓ stringr 1.4.0
    ## ✓ readr   2.0.1     ✓ forcats 0.5.1

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
library(survey)
```

    ## Loading required package: grid

    ## Loading required package: Matrix

    ## 
    ## Attaching package: 'Matrix'

    ## The following objects are masked from 'package:tidyr':
    ## 
    ##     expand, pack, unpack

    ## Loading required package: survival

    ## 
    ## Attaching package: 'survey'

    ## The following object is masked from 'package:graphics':
    ## 
    ##     dotchart

``` r
yrbss_state_a <- readRDS("data/2019 states a-m.rds")
yrbss_state_z <- readRDS("data/2019 states n-z.rds")
yrbss_state = rbind(yrbss_state_a,yrbss_state_z)
yrbss_state = as_tibble(yrbss_state)
yrbss_state
```

    ## # A tibble: 1,536,948 x 312
    ##    sitecode sitename    sitetype sitetypenum  year survyear weight stratum   psu
    ##    <chr>    <chr>       <chr>          <dbl> <dbl>    <dbl>  <dbl>   <dbl> <dbl>
    ##  1 AL       Alabama (A… State              2  1991        1   98.2       8     2
    ##  2 AL       Alabama (A… State              2  1991        1   69.2      15     2
    ##  3 AL       Alabama (A… State              2  1991        1   80.3      15     1
    ##  4 AL       Alabama (A… State              2  1991        1   66.5      20     2
    ##  5 AL       Alabama (A… State              2  1991        1   89.4       5     1
    ##  6 AL       Alabama (A… State              2  1991        1   59.3       1     1
    ##  7 AL       Alabama (A… State              2  1991        1   63.1       1     1
    ##  8 AL       Alabama (A… State              2  1991        1   63.6      15     1
    ##  9 AL       Alabama (A… State              2  1991        1   54.5       5     1
    ## 10 AL       Alabama (A… State              2  1991        1   73.9      12     1
    ## # … with 1,536,938 more rows, and 303 more variables: record <dbl>, age <dbl>,
    ## #   sex <dbl>, grade <dbl>, race4 <dbl>, race7 <dbl>, stheight <dbl>,
    ## #   stweight <dbl>, bmi <dbl>, bmipct <dbl>, qnobese <dbl>, qnowt <dbl>,
    ## #   q66 <chr>, q65 <chr>, sexid <dbl>, sexid2 <dbl>, sexpart <dbl>,
    ## #   sexpart2 <dbl>, q8 <chr>, q9 <chr>, q10 <chr>, q11 <chr>, q12 <chr>,
    ## #   q13 <chr>, q14 <chr>, q15 <chr>, q16 <chr>, q17 <chr>, q18 <chr>,
    ## #   q19 <chr>, q20 <chr>, q21 <chr>, q22 <chr>, q23 <chr>, q24 <chr>,
    ## #   q25 <chr>, q26 <chr>, q27 <chr>, q28 <chr>, q29 <chr>, q30 <chr>,
    ## #   q31 <chr>, q32 <chr>, q33 <chr>, q34 <chr>, q35 <chr>, q36 <chr>,
    ## #   q37 <chr>, q38 <chr>, q39 <chr>, q40 <chr>, q41 <chr>, q42 <chr>,
    ## #   q43 <chr>, q44 <chr>, q45 <chr>, q46 <chr>, q47 <chr>, q48 <chr>,
    ## #   q49 <chr>, q50 <chr>, q51 <chr>, q52 <chr>, q53 <chr>, q54 <chr>,
    ## #   q55 <chr>, q56 <chr>, q57 <chr>, q58 <chr>, q59 <chr>, q60 <chr>,
    ## #   q61 <chr>, q62 <chr>, q63 <chr>, q64 <chr>, q67 <chr>, q68 <chr>,
    ## #   q69 <chr>, q70 <chr>, q71 <chr>, q72 <chr>, q73 <chr>, q74 <chr>,
    ## #   q75 <chr>, q76 <chr>, q77 <chr>, q78 <chr>, q79 <chr>, q80 <chr>,
    ## #   q81 <chr>, q82 <chr>, q83 <chr>, q84 <chr>, q85 <chr>, q86 <chr>,
    ## #   q87 <chr>, q88 <chr>, q89 <chr>, qn8 <dbl>, qn9 <dbl>, …

### 01～03

``` r
yrbss_state
```

    ## # A tibble: 1,536,948 x 312
    ##    sitecode sitename    sitetype sitetypenum  year survyear weight stratum   psu
    ##    <chr>    <chr>       <chr>          <dbl> <dbl>    <dbl>  <dbl>   <dbl> <dbl>
    ##  1 AL       Alabama (A… State              2  1991        1   98.2       8     2
    ##  2 AL       Alabama (A… State              2  1991        1   69.2      15     2
    ##  3 AL       Alabama (A… State              2  1991        1   80.3      15     1
    ##  4 AL       Alabama (A… State              2  1991        1   66.5      20     2
    ##  5 AL       Alabama (A… State              2  1991        1   89.4       5     1
    ##  6 AL       Alabama (A… State              2  1991        1   59.3       1     1
    ##  7 AL       Alabama (A… State              2  1991        1   63.1       1     1
    ##  8 AL       Alabama (A… State              2  1991        1   63.6      15     1
    ##  9 AL       Alabama (A… State              2  1991        1   54.5       5     1
    ## 10 AL       Alabama (A… State              2  1991        1   73.9      12     1
    ## # … with 1,536,938 more rows, and 303 more variables: record <dbl>, age <dbl>,
    ## #   sex <dbl>, grade <dbl>, race4 <dbl>, race7 <dbl>, stheight <dbl>,
    ## #   stweight <dbl>, bmi <dbl>, bmipct <dbl>, qnobese <dbl>, qnowt <dbl>,
    ## #   q66 <chr>, q65 <chr>, sexid <dbl>, sexid2 <dbl>, sexpart <dbl>,
    ## #   sexpart2 <dbl>, q8 <chr>, q9 <chr>, q10 <chr>, q11 <chr>, q12 <chr>,
    ## #   q13 <chr>, q14 <chr>, q15 <chr>, q16 <chr>, q17 <chr>, q18 <chr>,
    ## #   q19 <chr>, q20 <chr>, q21 <chr>, q22 <chr>, q23 <chr>, q24 <chr>,
    ## #   q25 <chr>, q26 <chr>, q27 <chr>, q28 <chr>, q29 <chr>, q30 <chr>,
    ## #   q31 <chr>, q32 <chr>, q33 <chr>, q34 <chr>, q35 <chr>, q36 <chr>,
    ## #   q37 <chr>, q38 <chr>, q39 <chr>, q40 <chr>, q41 <chr>, q42 <chr>,
    ## #   q43 <chr>, q44 <chr>, q45 <chr>, q46 <chr>, q47 <chr>, q48 <chr>,
    ## #   q49 <chr>, q50 <chr>, q51 <chr>, q52 <chr>, q53 <chr>, q54 <chr>,
    ## #   q55 <chr>, q56 <chr>, q57 <chr>, q58 <chr>, q59 <chr>, q60 <chr>,
    ## #   q61 <chr>, q62 <chr>, q63 <chr>, q64 <chr>, q67 <chr>, q68 <chr>,
    ## #   q69 <chr>, q70 <chr>, q71 <chr>, q72 <chr>, q73 <chr>, q74 <chr>,
    ## #   q75 <chr>, q76 <chr>, q77 <chr>, q78 <chr>, q79 <chr>, q80 <chr>,
    ## #   q81 <chr>, q82 <chr>, q83 <chr>, q84 <chr>, q85 <chr>, q86 <chr>,
    ## #   q87 <chr>, q88 <chr>, q89 <chr>, qn8 <dbl>, qn9 <dbl>, …

### 05～07

``` r
yrbss_state
```

    ## # A tibble: 1,536,948 x 312
    ##    sitecode sitename    sitetype sitetypenum  year survyear weight stratum   psu
    ##    <chr>    <chr>       <chr>          <dbl> <dbl>    <dbl>  <dbl>   <dbl> <dbl>
    ##  1 AL       Alabama (A… State              2  1991        1   98.2       8     2
    ##  2 AL       Alabama (A… State              2  1991        1   69.2      15     2
    ##  3 AL       Alabama (A… State              2  1991        1   80.3      15     1
    ##  4 AL       Alabama (A… State              2  1991        1   66.5      20     2
    ##  5 AL       Alabama (A… State              2  1991        1   89.4       5     1
    ##  6 AL       Alabama (A… State              2  1991        1   59.3       1     1
    ##  7 AL       Alabama (A… State              2  1991        1   63.1       1     1
    ##  8 AL       Alabama (A… State              2  1991        1   63.6      15     1
    ##  9 AL       Alabama (A… State              2  1991        1   54.5       5     1
    ## 10 AL       Alabama (A… State              2  1991        1   73.9      12     1
    ## # … with 1,536,938 more rows, and 303 more variables: record <dbl>, age <dbl>,
    ## #   sex <dbl>, grade <dbl>, race4 <dbl>, race7 <dbl>, stheight <dbl>,
    ## #   stweight <dbl>, bmi <dbl>, bmipct <dbl>, qnobese <dbl>, qnowt <dbl>,
    ## #   q66 <chr>, q65 <chr>, sexid <dbl>, sexid2 <dbl>, sexpart <dbl>,
    ## #   sexpart2 <dbl>, q8 <chr>, q9 <chr>, q10 <chr>, q11 <chr>, q12 <chr>,
    ## #   q13 <chr>, q14 <chr>, q15 <chr>, q16 <chr>, q17 <chr>, q18 <chr>,
    ## #   q19 <chr>, q20 <chr>, q21 <chr>, q22 <chr>, q23 <chr>, q24 <chr>,
    ## #   q25 <chr>, q26 <chr>, q27 <chr>, q28 <chr>, q29 <chr>, q30 <chr>,
    ## #   q31 <chr>, q32 <chr>, q33 <chr>, q34 <chr>, q35 <chr>, q36 <chr>,
    ## #   q37 <chr>, q38 <chr>, q39 <chr>, q40 <chr>, q41 <chr>, q42 <chr>,
    ## #   q43 <chr>, q44 <chr>, q45 <chr>, q46 <chr>, q47 <chr>, q48 <chr>,
    ## #   q49 <chr>, q50 <chr>, q51 <chr>, q52 <chr>, q53 <chr>, q54 <chr>,
    ## #   q55 <chr>, q56 <chr>, q57 <chr>, q58 <chr>, q59 <chr>, q60 <chr>,
    ## #   q61 <chr>, q62 <chr>, q63 <chr>, q64 <chr>, q67 <chr>, q68 <chr>,
    ## #   q69 <chr>, q70 <chr>, q71 <chr>, q72 <chr>, q73 <chr>, q74 <chr>,
    ## #   q75 <chr>, q76 <chr>, q77 <chr>, q78 <chr>, q79 <chr>, q80 <chr>,
    ## #   q81 <chr>, q82 <chr>, q83 <chr>, q84 <chr>, q85 <chr>, q86 <chr>,
    ## #   q87 <chr>, q88 <chr>, q89 <chr>, qn8 <dbl>, qn9 <dbl>, …

### 09～11

``` r
yrbss_state
```

    ## # A tibble: 1,536,948 x 312
    ##    sitecode sitename    sitetype sitetypenum  year survyear weight stratum   psu
    ##    <chr>    <chr>       <chr>          <dbl> <dbl>    <dbl>  <dbl>   <dbl> <dbl>
    ##  1 AL       Alabama (A… State              2  1991        1   98.2       8     2
    ##  2 AL       Alabama (A… State              2  1991        1   69.2      15     2
    ##  3 AL       Alabama (A… State              2  1991        1   80.3      15     1
    ##  4 AL       Alabama (A… State              2  1991        1   66.5      20     2
    ##  5 AL       Alabama (A… State              2  1991        1   89.4       5     1
    ##  6 AL       Alabama (A… State              2  1991        1   59.3       1     1
    ##  7 AL       Alabama (A… State              2  1991        1   63.1       1     1
    ##  8 AL       Alabama (A… State              2  1991        1   63.6      15     1
    ##  9 AL       Alabama (A… State              2  1991        1   54.5       5     1
    ## 10 AL       Alabama (A… State              2  1991        1   73.9      12     1
    ## # … with 1,536,938 more rows, and 303 more variables: record <dbl>, age <dbl>,
    ## #   sex <dbl>, grade <dbl>, race4 <dbl>, race7 <dbl>, stheight <dbl>,
    ## #   stweight <dbl>, bmi <dbl>, bmipct <dbl>, qnobese <dbl>, qnowt <dbl>,
    ## #   q66 <chr>, q65 <chr>, sexid <dbl>, sexid2 <dbl>, sexpart <dbl>,
    ## #   sexpart2 <dbl>, q8 <chr>, q9 <chr>, q10 <chr>, q11 <chr>, q12 <chr>,
    ## #   q13 <chr>, q14 <chr>, q15 <chr>, q16 <chr>, q17 <chr>, q18 <chr>,
    ## #   q19 <chr>, q20 <chr>, q21 <chr>, q22 <chr>, q23 <chr>, q24 <chr>,
    ## #   q25 <chr>, q26 <chr>, q27 <chr>, q28 <chr>, q29 <chr>, q30 <chr>,
    ## #   q31 <chr>, q32 <chr>, q33 <chr>, q34 <chr>, q35 <chr>, q36 <chr>,
    ## #   q37 <chr>, q38 <chr>, q39 <chr>, q40 <chr>, q41 <chr>, q42 <chr>,
    ## #   q43 <chr>, q44 <chr>, q45 <chr>, q46 <chr>, q47 <chr>, q48 <chr>,
    ## #   q49 <chr>, q50 <chr>, q51 <chr>, q52 <chr>, q53 <chr>, q54 <chr>,
    ## #   q55 <chr>, q56 <chr>, q57 <chr>, q58 <chr>, q59 <chr>, q60 <chr>,
    ## #   q61 <chr>, q62 <chr>, q63 <chr>, q64 <chr>, q67 <chr>, q68 <chr>,
    ## #   q69 <chr>, q70 <chr>, q71 <chr>, q72 <chr>, q73 <chr>, q74 <chr>,
    ## #   q75 <chr>, q76 <chr>, q77 <chr>, q78 <chr>, q79 <chr>, q80 <chr>,
    ## #   q81 <chr>, q82 <chr>, q83 <chr>, q84 <chr>, q85 <chr>, q86 <chr>,
    ## #   q87 <chr>, q88 <chr>, q89 <chr>, qn8 <dbl>, qn9 <dbl>, …

### 13～15

``` r
yrbss_state
```

    ## # A tibble: 1,536,948 x 312
    ##    sitecode sitename    sitetype sitetypenum  year survyear weight stratum   psu
    ##    <chr>    <chr>       <chr>          <dbl> <dbl>    <dbl>  <dbl>   <dbl> <dbl>
    ##  1 AL       Alabama (A… State              2  1991        1   98.2       8     2
    ##  2 AL       Alabama (A… State              2  1991        1   69.2      15     2
    ##  3 AL       Alabama (A… State              2  1991        1   80.3      15     1
    ##  4 AL       Alabama (A… State              2  1991        1   66.5      20     2
    ##  5 AL       Alabama (A… State              2  1991        1   89.4       5     1
    ##  6 AL       Alabama (A… State              2  1991        1   59.3       1     1
    ##  7 AL       Alabama (A… State              2  1991        1   63.1       1     1
    ##  8 AL       Alabama (A… State              2  1991        1   63.6      15     1
    ##  9 AL       Alabama (A… State              2  1991        1   54.5       5     1
    ## 10 AL       Alabama (A… State              2  1991        1   73.9      12     1
    ## # … with 1,536,938 more rows, and 303 more variables: record <dbl>, age <dbl>,
    ## #   sex <dbl>, grade <dbl>, race4 <dbl>, race7 <dbl>, stheight <dbl>,
    ## #   stweight <dbl>, bmi <dbl>, bmipct <dbl>, qnobese <dbl>, qnowt <dbl>,
    ## #   q66 <chr>, q65 <chr>, sexid <dbl>, sexid2 <dbl>, sexpart <dbl>,
    ## #   sexpart2 <dbl>, q8 <chr>, q9 <chr>, q10 <chr>, q11 <chr>, q12 <chr>,
    ## #   q13 <chr>, q14 <chr>, q15 <chr>, q16 <chr>, q17 <chr>, q18 <chr>,
    ## #   q19 <chr>, q20 <chr>, q21 <chr>, q22 <chr>, q23 <chr>, q24 <chr>,
    ## #   q25 <chr>, q26 <chr>, q27 <chr>, q28 <chr>, q29 <chr>, q30 <chr>,
    ## #   q31 <chr>, q32 <chr>, q33 <chr>, q34 <chr>, q35 <chr>, q36 <chr>,
    ## #   q37 <chr>, q38 <chr>, q39 <chr>, q40 <chr>, q41 <chr>, q42 <chr>,
    ## #   q43 <chr>, q44 <chr>, q45 <chr>, q46 <chr>, q47 <chr>, q48 <chr>,
    ## #   q49 <chr>, q50 <chr>, q51 <chr>, q52 <chr>, q53 <chr>, q54 <chr>,
    ## #   q55 <chr>, q56 <chr>, q57 <chr>, q58 <chr>, q59 <chr>, q60 <chr>,
    ## #   q61 <chr>, q62 <chr>, q63 <chr>, q64 <chr>, q67 <chr>, q68 <chr>,
    ## #   q69 <chr>, q70 <chr>, q71 <chr>, q72 <chr>, q73 <chr>, q74 <chr>,
    ## #   q75 <chr>, q76 <chr>, q77 <chr>, q78 <chr>, q79 <chr>, q80 <chr>,
    ## #   q81 <chr>, q82 <chr>, q83 <chr>, q84 <chr>, q85 <chr>, q86 <chr>,
    ## #   q87 <chr>, q88 <chr>, q89 <chr>, qn8 <dbl>, qn9 <dbl>, …

### 17～19

``` r
yrbss_state
```

    ## # A tibble: 1,536,948 x 312
    ##    sitecode sitename    sitetype sitetypenum  year survyear weight stratum   psu
    ##    <chr>    <chr>       <chr>          <dbl> <dbl>    <dbl>  <dbl>   <dbl> <dbl>
    ##  1 AL       Alabama (A… State              2  1991        1   98.2       8     2
    ##  2 AL       Alabama (A… State              2  1991        1   69.2      15     2
    ##  3 AL       Alabama (A… State              2  1991        1   80.3      15     1
    ##  4 AL       Alabama (A… State              2  1991        1   66.5      20     2
    ##  5 AL       Alabama (A… State              2  1991        1   89.4       5     1
    ##  6 AL       Alabama (A… State              2  1991        1   59.3       1     1
    ##  7 AL       Alabama (A… State              2  1991        1   63.1       1     1
    ##  8 AL       Alabama (A… State              2  1991        1   63.6      15     1
    ##  9 AL       Alabama (A… State              2  1991        1   54.5       5     1
    ## 10 AL       Alabama (A… State              2  1991        1   73.9      12     1
    ## # … with 1,536,938 more rows, and 303 more variables: record <dbl>, age <dbl>,
    ## #   sex <dbl>, grade <dbl>, race4 <dbl>, race7 <dbl>, stheight <dbl>,
    ## #   stweight <dbl>, bmi <dbl>, bmipct <dbl>, qnobese <dbl>, qnowt <dbl>,
    ## #   q66 <chr>, q65 <chr>, sexid <dbl>, sexid2 <dbl>, sexpart <dbl>,
    ## #   sexpart2 <dbl>, q8 <chr>, q9 <chr>, q10 <chr>, q11 <chr>, q12 <chr>,
    ## #   q13 <chr>, q14 <chr>, q15 <chr>, q16 <chr>, q17 <chr>, q18 <chr>,
    ## #   q19 <chr>, q20 <chr>, q21 <chr>, q22 <chr>, q23 <chr>, q24 <chr>,
    ## #   q25 <chr>, q26 <chr>, q27 <chr>, q28 <chr>, q29 <chr>, q30 <chr>,
    ## #   q31 <chr>, q32 <chr>, q33 <chr>, q34 <chr>, q35 <chr>, q36 <chr>,
    ## #   q37 <chr>, q38 <chr>, q39 <chr>, q40 <chr>, q41 <chr>, q42 <chr>,
    ## #   q43 <chr>, q44 <chr>, q45 <chr>, q46 <chr>, q47 <chr>, q48 <chr>,
    ## #   q49 <chr>, q50 <chr>, q51 <chr>, q52 <chr>, q53 <chr>, q54 <chr>,
    ## #   q55 <chr>, q56 <chr>, q57 <chr>, q58 <chr>, q59 <chr>, q60 <chr>,
    ## #   q61 <chr>, q62 <chr>, q63 <chr>, q64 <chr>, q67 <chr>, q68 <chr>,
    ## #   q69 <chr>, q70 <chr>, q71 <chr>, q72 <chr>, q73 <chr>, q74 <chr>,
    ## #   q75 <chr>, q76 <chr>, q77 <chr>, q78 <chr>, q79 <chr>, q80 <chr>,
    ## #   q81 <chr>, q82 <chr>, q83 <chr>, q84 <chr>, q85 <chr>, q86 <chr>,
    ## #   q87 <chr>, q88 <chr>, q89 <chr>, qn8 <dbl>, qn9 <dbl>, …
