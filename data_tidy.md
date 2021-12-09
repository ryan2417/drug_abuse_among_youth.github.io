Data tidy
================

``` r
library(tidyverse)
library(survey)
library(viridis)
library(table1)
library(kableExtra)

knitr::opts_chunk$set(
  warning = FALSE,
  message = FALSE,
  echo = FALSE
)

theme_set(theme_minimal() + theme(legend.position = "bottom"))

options(
  ggplot2.continuous.colour = "viridis",
  ggplot2.continuous.fill = "viridis"
)

scale_colour_discrete = scale_colour_viridis_d(option = "viridis")
scale_fill_discrete = scale_fill_viridis_d(option = "viridis")
```
