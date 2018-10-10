p8105\_hw3\_ak4123
================

``` r
library(p8105.datasets)
data("brfss_smart2010")

brfss_data = brfss_smart2010 %>% 
  janitor::clean_names() %>% 
  filter(topic == "Overall Health") %>% 
  filter(response == "Excellent"|response == "Very good"|response =="Good"|response =="Fair"|response == "Poor") %>% 
  mutate(response = factor(response, levels = ordered("Excellent", "Very good", "Good", "Fair", "Poor")))
```

``` r
brfss_data %>%
  filter (year == 2002) %>% 
  group_by(locationdesc) %>%
  group_by(locationabbr) %>% 
  count(locationabbr)
```

    ## # A tibble: 49 x 2
    ## # Groups:   locationabbr [49]
    ##    locationabbr     n
    ##    <chr>        <int>
    ##  1 AK               5
    ##  2 AL               5
    ##  3 AR               5
    ##  4 AZ              10
    ##  5 CA               5
    ##  6 CO              20
    ##  7 CT              35
    ##  8 DC               5
    ##  9 DE              15
    ## 10 FL              35
    ## # ... with 39 more rows
