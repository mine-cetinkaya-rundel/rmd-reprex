
``` r
iris %>%
  group_by(Species) %>%
  mutate(mean_sw = mean(Sepal.Width))
```

    ## Error in iris %>% group_by(Species) %>% mutate(mean_sw = mean(Sepal.Width)): could not find function "%>%"
