Download\_dataset
================

This is the file that you can use to download the dataset we use to your
local computer. For more information, you can refer to *Analyze Survey
Data for Free* which is listed as the third reference in `proposal.Rmd`.

``` r
library(lodown)
library(tidyverse)
library(survey)

# examine all available YRBSS microdata files
yrbss_cat =
    get_catalog( "yrbss" ,
        output_dir = file.path( path.expand( "~" ) , "YRBSS" ) ) 

# 2019 only
yrbss_cat = filter( yrbss_cat , year == 2019 )

# state only
yrbss_cat = filter(yrbss_cat , dat_url %in% c("https://ftp.cdc.gov/pub/data/yrbs/SADC_2019/sadc_2019_state_a_m.dat", "https://ftp.cdc.gov/pub/data/yrbs/SADC_2019/sadc_2019_state_n_z.dat"))

# download the microdata to your local computer
yrbss_cat = lodown( "yrbss" , yrbss_cat )
```
