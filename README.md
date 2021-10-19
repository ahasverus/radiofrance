
<!-- README.md is generated from README.Rmd. Please edit that file -->

# franceinter <img src="man/figures/hexsticker.png" height="120" align="right"/>

<!-- badges: start -->

[![R CMD
Check](https://github.com/ahasverus/franceinter/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/ahasverus/franceinter/actions/workflows/R-CMD-check.yaml)
[![Website
deployment](https://github.com/ahasverus/franceinter/actions/workflows/pkgdown.yaml/badge.svg)](https://github.com/ahasverus/franceinter/actions/workflows/pkgdown.yaml)
[![Update
metadata](https://github.com/ahasverus/franceinter/actions/workflows/update-podcasts.yml/badge.svg)](https://github.com/ahasverus/franceinter/actions/workflows/update-podcasts.yml)
[![License:
MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://choosealicense.com/licenses/mit/)
<!-- badges: end -->

The goal of the R package `franceinter` is to retrieve France Inter
podcasts information and to download MP3 episodes.

## Installation

You can install the development version from
[GitHub](https://github.com/) with:

``` r
# install.packages("remotes")
remotes::install_github("ahasverus/franceinter")
```

Then you can attach the package `franceinter`:

``` r
library("franceinter")
```

## Usage

``` r
## Create a folder to store results ----

path <- "Podcasts/"
dir.create(path)


## Get podcasts name ----

podcasts <- list_podcasts()
podcast  <- podcasts[3, ]

##                    podcast start_date end_date
## 3 la-chronique-de-waly-dia 2020-10-05     <NA>


## Retrieve episodes information ----

tab <- get_metadata(podcast    = podcast$"podcast", 
                    start_date = podcast$"start_date", 
                    end_date   = podcast$"end_date", 
                    path = path)

## ✓ Adding 15 new episodes to './Podcasts/la-chronique-de-waly-dia.csv' 


## Create a M3U playlist ----

add_m3u(tab, podcast$"podcast", path = path)

## ✓ Writing './Podcasts/la-chronique-de-waly-dia.m3u' file
```

The `m3u` file can be open with VLC to stream all episodes. To add new
episodes, just re-run this block code. A function to download mp3 will
be available soon.

Users can add custom (France Inter) podcasts by creating a data frame
with one row and the following columns: `podcast`, `start_date`, and
`end_date` (can be `NA`).

## Citation

Please cite this package as:

> Casajus Nicolas (2021) franceinter: An R package to retrieve France
> Inter podcasts. R package version 0.0.0.9000.

## Code of Conduct

Please note that the `franceinter` project is released with a
[Contributor Code of
Conduct](https://contributor-covenant.org/version/2/0/CODE_OF_CONDUCT.html).
By contributing to this project, you agree to abide by its terms.