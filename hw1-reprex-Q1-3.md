
``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────────── tidyverse 1.2.1 ──

    ## ✔ ggplot2 3.2.1     ✔ purrr   0.3.3
    ## ✔ tibble  2.1.3     ✔ dplyr   0.8.3
    ## ✔ tidyr   1.0.0     ✔ stringr 1.4.0
    ## ✔ readr   1.3.1     ✔ forcats 0.4.0

    ## ── Conflicts ────────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
iris_modified <- iris %>%
  mutate(
    sepal_ratio = Sepal.Width / Sepal.Length,
    petal_ratio = Petal.Width / Petal.Length
    )
```

``` r
ggplot(iris_modified, aes(x = sepal_ratio, y = petal_ratio, color = species)) +
  geom_point()
```

    ## Error in FUN(X[[i]], ...): object 'species' not found

![](hw1-reprex-Q1-3_files/figure-gfm/plot-ratios-1.png)<!-- -->
