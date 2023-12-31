
<!-- README.md is generated from README.Rmd. Please edit that file -->

# b2lpuumala

Lauren Puumala  
2023-11-10  
<!-- badges: start --> <!-- badges: end -->

## Description

This package contains a function called `count_obs` that can be used to
count the number of observations of a categorical variable or
combinations of categorical variables in a data frame. It returns the
results as a tibble. Relevant documentation, tests, and examples for
this function are included in this package as well.

**Function specifications:**  
- Parameters:  
- `data`: the data frame  
- `group_vars`: categorical variables in `data` to be used for grouping.
Grouping variables must belong to one of the following classes:
character, factor, or date.  
- Result: a tibble tabulating the number of observations of the
specified categorical grouping variable(s) in `data`.

**Files and folders in this repo:**  
- **.gitignore:** text file to specify which files should not be tracked
by Git  
- **.Rbuildignore:** exclude files from being put in the package  
- **b2lpuumala.Rproj:** Rstudio project file for this assignment  
- **DESCRIPTION:** metadata about the package  
- **LICENSE:** copyright info  
- **LICESE.md:** .md file containing MIT license details  
- **man:** folder containing function documentation  
- **NAMESPACE:** declares which functions this package exports for
external use and which functions it imports from external packages  
- **NEWS.md:** news file with development notes  
- **R:** folder containing R files with function definitions  
- **README.Rmd:** this README file (R Markdown version)  
- **README.md:** this README file (GitHub Markdown version)  
- **tests:** folder containing function tests

## Demonstrated Usage

``` r
library(b2lpuumala)

#CORRECT USAGE
#Using the vancouver_trees dataset from datateachr
#One grouping variable
count_obs(datateachr::vancouver_trees, "neighbourhood_name")
#> # A tibble: 22 × 2
#>    neighbourhood_name       num_obs
#>    <chr>                      <int>
#>  1 ARBUTUS-RIDGE               5169
#>  2 DOWNTOWN                    5159
#>  3 DUNBAR-SOUTHLANDS           9415
#>  4 FAIRVIEW                    4002
#>  5 GRANDVIEW-WOODLAND          6703
#>  6 HASTINGS-SUNRISE           10547
#>  7 KENSINGTON-CEDAR COTTAGE   11042
#>  8 KERRISDALE                  6936
#>  9 KILLARNEY                   6148
#> 10 KITSILANO                   8115
#> # ℹ 12 more rows

#Multiple grouping variables
count_obs(datateachr::vancouver_trees, c("neighbourhood_name", "genus_name", "species_name"))
#> # A tibble: 3,713 × 4
#>    neighbourhood_name genus_name species_name num_obs
#>    <chr>              <chr>      <chr>          <int>
#>  1 ARBUTUS-RIDGE      ABIES      GRANDIS           18
#>  2 ARBUTUS-RIDGE      ACER       CAMPESTRE        120
#>  3 ARBUTUS-RIDGE      ACER       CAPPADOCICUM       8
#>  4 ARBUTUS-RIDGE      ACER       CIRCINATUM         1
#>  5 ARBUTUS-RIDGE      ACER       FREEMANI   X      29
#>  6 ARBUTUS-RIDGE      ACER       GINNALA            5
#>  7 ARBUTUS-RIDGE      ACER       GRISEUM           52
#>  8 ARBUTUS-RIDGE      ACER       JAPONICUM          1
#>  9 ARBUTUS-RIDGE      ACER       MACROPHYLLUM      10
#> 10 ARBUTUS-RIDGE      ACER       NEGUNDO            4
#> # ℹ 3,703 more rows

#INCORRECT USAGE  
#Error is thrown when group_vars contains at least one variable that is the wrong class. See examples below.
count_obs(datateachr::vancouver_trees, "diameter")
#> Error in count_obs(datateachr::vancouver_trees, "diameter"): Incorrect grouping variable class. Ensure all group_vars are of class chr, fct, or date.

count_obs(datateachr::vancouver_trees, c("neighbourhood_name", "diameter"))
#> Error in count_obs(datateachr::vancouver_trees, c("neighbourhood_name", : Incorrect grouping variable class. Ensure all group_vars are of class chr, fct, or date.
```

## Installation

You can install the development version of b2lpuumala from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("stat545ubc-2023/b2lpuumala", ref = "0.1.0")
```
