
<!-- badges: start -->
[![tic](https://github.com/ropensci/nasapower/workflows/tic/badge.svg?branch=master)](https://github.com/ropensci/nasapower/actions)
[![codecov](https://codecov.io/gh/ropensci/nasapower/branch/master/graph/badge.svg)](https://codecov.io/gh/ropensci/nasapower)
[![DOI](https://zenodo.org/badge/109224461.svg)](https://zenodo.org/badge/latestdoi/109224461)
[![Project Status: Active – The project has reached a stable, usable
state and is being actively
developed.](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)
[![peer-review](https://badges.ropensci.org/155_status.svg)](https://github.com/ropensci/software-review/issues/155)
[![DOI](http://joss.theoj.org/papers/10.21105/joss.01035/status.svg)](https://doi.org/10.21105/joss.01035)
[![CRAN](http://www.r-pkg.org/badges/version/nasapower)](https://CRAN.R-project.org/package=nasapower)
<!-- badges: end -->

# *nasapower*: NASA POWER Global Meteorology, Surface Solar Energy and Climatology Data Client <img align="right" src="man/figures/logo.png">

*nasapower* aims to make it quick and easy to automate downloading [NASA-POWER](https://power.larc.nasa.gov) global meteorology, surface solar energy and climatology data in your R session as a tidy data frame `tibble` object for analysis and use in modelling or other purposes.
POWER (Prediction Of Worldwide Energy Resource) data are freely available for download at a resolution of 1/2 arc degree longitude by 1/2 arc degree latitude.

Please see <https://power.larc.nasa.gov/> for more on the data and other ways to access it and other forms of data available, *e.g.*, your web browser or an ESRI REST API.

### Quick start

*nasapower* can easily be installed using the following code.

#### From CRAN

The stable version is available through CRAN.

``` r
install.packages("nasapower")
```

#### From GitHub for the version in-development

A development version that may have new features or bug fixes is available through GitHub.

``` r
if (!require(devtools)) {
  install.packages("devtools")
}

devtools::install_github("ropensci/nasapower",
                         build_vignettes = TRUE
)
```

### Example

Fetch daily “AG” community temperature, relative humidity and precipitation for January 1 1985 for Kingsthorpe, Queensland, Australia.

``` r
library(nasapower)
daily_ag <- get_power(community = "AG",
                      lonlat = c(151.81, -27.48),
                      pars = c("RH2M", "T2M", "PRECTOT"),
                      dates = "1985-01-01",
                      temporal_average = "DAILY"
                      )
                    
daily_ag
#> NASA/POWER SRB/FLASHFlux/MERRA2/GEOS 5.12.4 (FP-IT) 0.5 x 0.5 Degree Daily Averaged Data  
#>  Dates (month/day/year): 01/01/1985 through 01/01/1985  
#>  Location: Latitude  -27.48   Longitude 151.81  
#>  Elevation from MERRA-2: Average for 1/2x1/2 degree lat/lon region = 434.55 meters   Site = na  
#>  Climate zone: na (reference Briggs et al: http://www.energycodes.gov)  
#>  Value for missing model data cannot be computed or out of model availability range: -99  
#>  
#>  Parameters: 
#>  PRECTOT MERRA2 1/2x1/2 Precipitation (mm day-1) ;
#>  RH2M MERRA2 1/2x1/2 Relative Humidity at 2 Meters (%) ;
#>  T2M MERRA2 1/2x1/2 Temperature at 2 Meters (C)  
#>  
#> # A tibble: 1 x 10
#>     LON   LAT  YEAR    MM    DD   DOY YYYYMMDD    RH2M   T2M PRECTOT
#>   <dbl> <dbl> <dbl> <int> <int> <int> <date>     <dbl> <dbl>   <dbl>
#> 1  152. -27.5  1985     1     1     1 1985-01-01  48.9  25.1    1.07
```

## Documentation

More documentation is available in the vignette in your R session, `vignette("nasapower")` or available online, <https://docs.ropensci.org/nasapower/>.

## Use of POWER Data

While *nasapower* does not redistribute the data or provide it in any way, we encourage users to follow the requests of the POWER Project Team.

> When POWER data products are used in a publication, we request the
> following acknowledgement be included: “These data were obtained from
> the NASA Langley Research Center POWER Project funded through the NASA
> Earth Science Directorate Applied Science Program.”

## Meta

  - Please [report any issues or
    bugs](https://github.com/ropensci/nasapower/issues).

  - License: MIT

  - To cite *nasapower*, please use the output from `citation(package = "nasapower")`.

  - Please note that the *nasapower* project is released with a [Contributor Code of Conduct](https://github.com/ropensci/nasapower/blob/master/CONDUCT.md).
    By participating in the *nasapower* project you agree to abide by its terms.

  - The U.S. Earth System Research Laboratory, Physical Science Division of the National Atmospheric & Oceanic Administration (NOAA) maintains a list of gridded climate data sets that provide different data and different resolutions <https://psl.noaa.gov/data/gridded/>.

## References

<https://power.larc.nasa.gov>

<https://power.larc.nasa.gov/docs/methodology/>
