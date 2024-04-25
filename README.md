<!-- badges: start -->
[![GPLv3 License](https://img.shields.io/badge/License-GPL%20v3-yellow.svg)](https://opensource.org/licenses/)
[![R-CMD-check](https://github.com/billbillbilly/quickPWCR/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/billbillbilly/quickPWCR/actions/workflows/R-CMD-check.yaml)
![CRAN](https://www.r-pkg.org/badges/version/quickPWCR)
![monthly](https://cranlogs.r-pkg.org/badges/quickPWCR)
![total](https://cranlogs.r-pkg.org/badges/grand-total/quickPWCR)
<!-- badges: end -->


# quickPWCR

<p align="left">

<img src="quickpwcr_hex.png" height="200">

</p>


## Introduction
A collection of functions for constructing large pairwised comparisons 
and rating them using Elo rating system with supporting parallel processing.
The method of random sample pairs is based on Reservoir Sampling.


## Installation 
``` r
# install the package from GitHub
devtools::install_github("billbillbilly/quickPWCR", dependencies=TRUE)
```

## Usage
``` r
# create a large group of players
players <- unique(round(runif(n=2000, min=1, max=50000), 0))
# Each player will be randomly paired with other 50 players 
pw <- quickPWCR::randompair(players = players, k = 100)


# Assume the 'left' column is for winners and 'right' column is for loser
elo_ratings <- quickPWCR::m_elo(pw, 
                       c('left', 'right'), 
                       elo_randomisations = 100, 
                       initial_rating = 100, 
                       k = 10, 
                       cores = 1)
```

## Note
The package currently does not support multi-core processing on Windows system. 

## Issues and bugs
If you discover a bug not associated with connection to the API that is
not already a [reported issue](https://github.com/billbillbilly/quickPWCR/issues), please [open
a new issue](https://github.com/billbillbilly/quickPWCR/issues/new)
providing a reproducible example.
