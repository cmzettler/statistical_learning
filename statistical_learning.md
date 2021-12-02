statistical learning
================

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──

    ## ✓ ggplot2 3.3.5     ✓ purrr   0.3.4
    ## ✓ tibble  3.1.5     ✓ dplyr   1.0.7
    ## ✓ tidyr   1.1.3     ✓ stringr 1.4.0
    ## ✓ readr   2.0.1     ✓ forcats 0.5.1

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
library(viridis)
```

    ## Loading required package: viridisLite

``` r
library(modelr)
library(mgcv)
```

    ## Loading required package: nlme

    ## 
    ## Attaching package: 'nlme'

    ## The following object is masked from 'package:dplyr':
    ## 
    ##     collapse

    ## This is mgcv 1.8-38. For overview type 'help("mgcv-package")'.

``` r
library(patchwork)

knitr::opts_chunk$set(
  fig.width = 6,
  fig.asp = .6,
  out.width = "90%"
)

theme_set(theme_minimal() + theme(legend.position = "bottom"))

options(
  ggplot2.continuous.colour = "viridis",
  ggplot2.continuous.fill = "viridis"
)

scale_colour_discrete = scale_colour_viridis_d
scale_fill_discrete = scale_fill_viridis_d
```

statistical learning = machine learning = AI

statistical learning is on a spectrum of tools to do data analysis

Learning from data - supervised learning: there’s an outcome that you
care about and what you learn depends on that outcome (regression,
lsaso, etc.) - unsupervised learning: you have data and you want to
learn stuff (find patterns, ID subgroups, etc.), don’t care about 1
specific outcome (clustering, etc.)

Regression - common understanding, interpretable coefficients,
inference/ p-values

Regression –&gt; Lasso - one drawback of regression is lack of
scalability (fewer model building options with lots of covariates) -
Lasso –&gt; useful when you have a lot of coefficients and a few strong
hypotheses “automatically” selects variables - Lasso adds a penalty on
the sum of all coefficients (minimize residual sum or squares (like
normal regression) and a penalty if your regression coefficients are
big) –&gt; working against each other - it’s regression + a penalty, but
the penalty has a big impact

-   if your penalty gets big, you push to 0 (delete coefficients,
    automatic variables selection)

Lasso drawbacks - no inference/ p-values - very different (if any)
interpretation - IF YOU HAVE A HYPTHESIS TO TEST, LASSO ISN’T YOUR
ANSWER

Tuning parameter selection - dial lambda up and down to decide how much
emphasis to put on the penalty piece - use cross validation
