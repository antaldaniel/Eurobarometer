
<!-- README.md is generated from README.Rmd. Please edit that file -->

# eurobarometer

<!-- badges: start -->

[![Travis build
status](https://travis-ci.com/antaldaniel/eurobarometer.svg?branch=master)](https://travis-ci.com/antaldaniel/eurobarometer)
[![Codecov test
coverage](https://codecov.io/gh/antaldaniel/eurobarometer/branch/master/graph/badge.svg)](https://codecov.io/gh/antaldaniel/eurobarometer?branch=master)
[![Project Status: Minimal or no implementation has been done yet, or
the repository is only intended to be a limited example, demo, or
proof-of-concept.](https://www.repostatus.org/badges/latest/concept.svg)](https://www.repostatus.org/#concept)
“[![license](https://img.shields.io/badge/license-GPL--3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0.en.html)”
“[![CRAN\_Status\_Badge](https://www.r-pkg.org/badges/version/eurobarometer)](https://cran.r-project.org/package=eurobarometer)”
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.3901724.svg)](https://doi.org/10.5281/zenodo.3901724)
[![Follow
author](https://img.shields.io/twitter/follow/antaldaniel.svg?style=social)](https://twitter.com/intent/follow?screen_name=antaldaniel)
[![Follow
contributor](https://img.shields.io/twitter/follow/martakolcz.svg?style=social)](https://twitter.com/martakolcz?lang=en)
<!-- badges: end -->

The goal of `eurobarometer` is converting Eurobarometer microdata files,
as stored by GESIS, into tidy R data frames and help common
pre-processing problems.

Please report all issues to
[github.com/antaldaniel/eurobarometer/issues](https://github.com/antaldaniel/eurobarometer/issues).

Pull requests are welcome on
[github.com/antaldaniel/eurobarometer](\(https://github.com/antaldaniel/eurobarometer/issues\))
from all potential contributors who abide by the terms of the
[Contributor Code of
Conduct](https://contributor-covenant.org/version/2/0/CODE_OF_CONDUCT.html).

If you use `eurobarometer` in your work, please [cite the
package](https://doi.org/10.5281/zenodo.3825700).

## Installation

At this moment you cannot install yet the package from
[CRAN](https://CRAN.R-project.org), but there is a development version
on [GitHub](https://github.com/):

``` r
# install.packages("devtools")
devtools::install_github("antaldaniel/eurobarometer")
```

## Data Preparation For Programmatic Use

The microdata of the European Commissions Eurobarometer surveys are
stored and accessible in [GESIS](https://www.gesis.org/home). They are
not ready for programmatic use in R or for joining into longitudinal
panels. We created this package to help this procedure following the
principles of reproducible research.

1.  We import the GESIS SPSS files with the help of the
    [haven](https://haven.tidyverse.org/) package. In order to preserve
    the metadata in the files (particularly variable- and value labels,
    and user-defined missing values) these are converted to labelled
    classes.

2.  We analyse the files with `gesis_metadata_create()` to understand
    what are the possible problems in the SPSS file and how to resolve
    them. (See: [Working With
    Metadata](http://eurobarometer.danielantal.eu/articles/metadata.html)
    or `vignette("metadata")`)

3.  We suggest various
    [naming](http://eurobarometer.danielantal.eu/articles/variable_names.html)
    and
    [harmonization](http://eurobarometer.danielantal.eu/articles/workflow.html)
    changes in the data as a data processing step. These suggested
    changes can be modified by the user.

4.  We convert the variables to a modified version of the
    `haven_labelled_spss` class that contains the harmonized values,
    harmonized labels, harmonized missing values codes of the variable
    with their history (original values, labels, and function applied to
    change them) for reproducibility. The
    [eurobarometer\_labelled](http://eurobarometer.danielantal.eu/articles/eurobarometer_class.html)
    class inherits most of the functionality of the packages
    [haven](https://haven.tidyverse.org/),
    [labelled](https://cran.r-project.org/web/packages/labelled/vignettes/intro_labelled.html)
    and are expected to work well with
    [sjlabelled](https://strengejacke.github.io/sjlabelled/articles/labelleddata.html).

<div class="figure" style="text-align: center">

<img src="C:/Users/Daniel Antal/OneDrive - Visegrad Investments/_package/eurobarometer/man/figures/README/labelled_workflow.png" alt="Workflow from 'Introduction to labelled by Joseph Larmaranged'" width="90%" />

<p class="caption">

Workflow from ‘Introduction to labelled by Joseph Larmaranged’

</p>

</div>

Our approach follows `Approach B` to allow the conversion of harmonized
and joined files back into SPSS.

5.  The
    [eurobarometer\_labelled](http://eurobarometer.danielantal.eu/articles/eurobarometer_class.html)
    class comes with simple methods that can convert all variables to
    the base R types of numeric or factor, and they are ready to be used
    with any R statistical packages and tidyverse data processing tools.
    Alternatively, they can be exported back to
    [SPSS](https://haven.tidyverse.org/reference/read_spss.html) or
    [Stata](https://haven.tidyverse.org/reference/read_dta.html) files
    with the functions of the [haven](https://haven.tidyverse.org/)
    package.

## Joining With Eurostat & Other Data Tables

  - The regional boundaries are consistently used, coded and named -
    this will be harmonized with the package
    [regions](http://regions.danielantal.eu/), which helps resolving
    common issues, and to properly join various Eurobarometer files with
    Eurostat data tables and Google data tables.

  - This will also allow you to create regional statistics from
    Eurobarometer microdata files.

## Code of Conduct

Please note that the `eurobarometer` project is released with a
[Contributor Code of
Conduct](https://contributor-covenant.org/version/2/0/CODE_OF_CONDUCT.html).
By contributing to this project, you agree to its terms.

## Disclaimer

The authors of this package are not affiliated with
[GESIS](https://www.gesis.org/home), or the producer of the
Eurobarometer surveys, or the European Commission. For more information
about the European Commission’s Eurobarometer history, visit the
European Commission’s [Public
Opinion](https://ec.europa.eu/commfrontoffice/publicopinion/index.cfm)
website.
