
# Notes

I managed to get {renv} set up and working in this analysis on my 2020 MacBook Air M1.
These are my notes on the process and my findings.

## System Changes

* Needed to set up custom "~/.R/Makevars" to compile packages on M1

```bash
FC      = /opt/homebrew/bin/gfortran
F77     = /opt/homebrew/bin/gfortran
FLIBS   = -L/opt/homebrew/bin/gcc-12/lib
````

## R Session and {renv} Settings

* Needed to set custom options for R session to compile {sf} using {renv}

```r
options(
  configure.args = c(
    "--with-sqlite3-lib=/opt/homebrew/opt/sqlite/lib",
    "--with-proj-lib=/opt/homebrew/opt/proj/lib"
  )
)

renv::restore()
```

* Reinitiated the {renv} environment with BioConductor like this,

```r
renv::init(bioconductor = "3.16")
````

Because BioConductor packages are not part of MRAN and {RVAideMemoire} is needed for "meta-analysis data Exploration.Rmd" and was not a part of the renv.lock file.


* Set {vegan} version to 2.4.3 in "renv.lock" and ran `renv::restore()` to install the proper version.

## Analysis

Setting my .Renviron up to have `MC_CORES=4`, meant that I could automatically use 4 cores when running {vegan} functions supporting parallel processing, _e.g._ `anosim()` or `adonis2()`, decreasing run time.

I'm still unable to use the `pairwise.perm.manova()` no matter what version of {MVAidememoire} I use, I always get this error.

```r
Error in `colnames<-`(`*tmp*`, value = colnames(lhs)) :
attempt to set 'colnames' on an object with less than two dimensions
```

Unfortunately, I don't know enough about these packages or the analysis to troubleshoot this very deeply.
I'd assumed it was as simple as a version and by going back in time with {renv} I'd be able to solve it.
But going back in time with both {vegan} and {MVAidememoire} does not solve the problem at all.
It still exists.

Note that `adonis()` is deprecated but not defunct, so it's still available in the latest version of {vegan}, see https://github.com/vegandevs/vegan/issues/523#issuecomment-1274903088.
So, my take is that there's another issue with the data structure that's unrelated to {renv} or R package versions in the analysis.

-a

## Colophon

### {renv} status

```r
> renv::status()
* The project is already synchronized with the lockfile.
```

### Session Info

```r
─ Session info ───────────────────────────────────────────────────────────────────────────────────
 setting  value
 version  R version 4.2.2 (2022-10-31)
 os       macOS Ventura 13.1
 system   aarch64, darwin20
 ui       RStudio
 language (EN)
 collate  en_AU.UTF-8
 ctype    en_AU.UTF-8
 tz       Australia/Perth
 date     2023-02-11
 rstudio  2022.12.0+353 Elsbeth Geranium (desktop)
 pandoc   3.0.1 @ /opt/homebrew/bin/pandoc

─ Packages ───────────────────────────────────────────────────────────────────────────────────────
 ! package       * version  date (UTC) lib source
 P abind           1.4-5    2016-07-21 [?] CRAN (R 4.2.0)
 P ade4          * 1.7-22   2023-02-06 [?] CRAN (R 4.2.0)
 P adegenet      * 2.1.4    2021-07-17 [?] CRAN (R 4.2.2)
 P ape           * 5.6-2    2022-03-02 [?] CRAN (R 4.2.0)
 P assertthat      0.2.1    2019-03-21 [?] CRAN (R 4.2.0)
 P backports       1.4.1    2021-12-13 [?] CRAN (R 4.2.0)
 P boot            1.3-28.1 2022-11-22 [?] CRAN (R 4.2.0)
 P broom           1.0.3    2023-01-25 [?] CRAN (R 4.2.0)
 P bslib           0.4.2    2022-12-16 [?] CRAN (R 4.2.0)
 P cachem          1.0.6    2021-08-19 [?] CRAN (R 4.2.0)
 P car             3.1-1    2022-10-19 [?] CRAN (R 4.2.0)
 P carData         3.0-5    2022-01-06 [?] CRAN (R 4.2.0)
 P cellranger      1.1.0    2016-07-27 [?] CRAN (R 4.2.0)
 P class           7.3-19   2021-05-03 [?] CRAN (R 4.2.2)
 P classInt        0.4-8    2022-09-29 [?] CRAN (R 4.2.0)
 P cli             3.6.0    2023-01-09 [?] CRAN (R 4.2.0)
 P cluster         2.1.2    2021-04-17 [?] CRAN (R 4.2.2)
 P colorspace      2.1-0    2023-01-23 [?] CRAN (R 4.2.0)
 P cowplot       * 1.1.1    2020-12-30 [?] CRAN (R 4.2.0)
 P crayon          1.5.2    2022-09-29 [?] CRAN (R 4.2.0)
 P crosstalk       1.2.0    2021-11-04 [?] CRAN (R 4.2.0)
 P data.table      1.14.6   2022-11-16 [?] CRAN (R 4.2.0)
 P DBI             1.1.3    2022-06-18 [?] CRAN (R 4.2.0)
 P dbplyr          2.3.0    2023-01-16 [?] CRAN (R 4.2.0)
 P deldir          1.0-6    2021-10-23 [?] CRAN (R 4.2.0)
 P digest          0.6.31   2022-12-11 [?] CRAN (R 4.2.0)
 P dplyr         * 1.1.0    2023-01-29 [?] CRAN (R 4.2.0)
 P DT            * 0.27     2023-01-17 [?] CRAN (R 4.2.0)
 P e1071           1.7-13   2023-02-01 [?] CRAN (R 4.2.0)
 P ellipse       * 0.4.3    2022-05-31 [?] CRAN (R 4.2.0)
 P ellipsis        0.3.2    2021-04-29 [?] CRAN (R 4.2.0)
 P fansi           1.0.4    2023-01-22 [?] CRAN (R 4.2.0)
 P farver          2.1.1    2022-07-06 [?] CRAN (R 4.2.0)
 P fastmap         1.1.0    2021-01-25 [?] CRAN (R 4.2.0)
 P forcats       * 1.0.0    2023-01-29 [?] CRAN (R 4.2.0)
 P fs              1.6.1    2023-02-06 [?] CRAN (R 4.2.0)
 P generics        0.1.3    2022-07-05 [?] CRAN (R 4.2.0)
 P ggplot2       * 3.4.1    2023-02-10 [?] CRAN (R 4.2.0)
 P ggpubr        * 0.4.0    2020-06-27 [?] CRAN (R 4.2.0)
 P ggsignif      * 0.6.4    2022-10-13 [?] CRAN (R 4.2.0)
 P glue            1.6.2    2022-02-24 [?] CRAN (R 4.2.0)
 P gtable          0.3.1    2022-09-01 [?] CRAN (R 4.2.0)
 P hagis         * 3.1.4    2022-08-15 [?] CRAN (R 4.2.0)
 P haven           2.5.1    2022-08-22 [?] CRAN (R 4.2.0)
 P here          * 1.0.1    2020-12-13 [?] CRAN (R 4.2.0)
 P hms             1.1.2    2022-08-19 [?] CRAN (R 4.2.0)
 P htmltools       0.5.4    2022-12-07 [?] CRAN (R 4.2.0)
 P htmlwidgets     1.6.1    2023-01-07 [?] CRAN (R 4.2.0)
 P httpuv          1.6.8    2023-01-12 [?] CRAN (R 4.2.0)
 P httr            1.4.4    2022-08-17 [?] CRAN (R 4.2.0)
 P igraph          1.4.0    2023-02-10 [?] CRAN (R 4.2.0)
 P jquerylib       0.1.4    2021-04-26 [?] CRAN (R 4.2.0)
 P jsonlite        1.8.4    2022-12-06 [?] CRAN (R 4.2.0)
 P KernSmooth      2.23-20  2021-05-03 [?] CRAN (R 4.2.0)
 P knitr           1.42     2023-01-25 [?] CRAN (R 4.2.0)
 P labeling        0.4.2    2020-10-20 [?] CRAN (R 4.2.0)
 P later           1.3.0    2021-08-18 [?] CRAN (R 4.2.0)
 P lattice       * 0.20-44  2021-05-02 [?] CRAN (R 4.2.2)
 P lifecycle       1.0.3    2022-10-07 [?] CRAN (R 4.2.0)
 P lubridate       1.9.1    2023-01-24 [?] CRAN (R 4.2.2)
 P magrittr        2.0.3    2022-03-30 [?] CRAN (R 4.2.0)
 P MASS            7.3-58.2 2023-01-23 [?] CRAN (R 4.2.0)
 P Matrix          1.5-3    2022-11-11 [?] CRAN (R 4.2.0)
 P mgcv            1.8-36   2021-06-01 [?] CRAN (R 4.2.2)
 P mime            0.12     2021-09-28 [?] CRAN (R 4.2.0)
 P modelr          0.1.10   2022-11-11 [?] CRAN (R 4.2.0)
 P munsell         0.5.0    2018-06-12 [?] CRAN (R 4.2.0)
 P nlme            3.1-162  2023-01-31 [?] CRAN (R 4.2.0)
 P openxlsx      * 4.2.4    2021-06-16 [?] CRAN (R 4.2.2)
 P pander        * 0.6.5    2022-03-18 [?] CRAN (R 4.2.0)
 P permute       * 0.9-7    2022-01-27 [?] CRAN (R 4.2.0)
 P pillar          1.8.1    2022-08-19 [?] CRAN (R 4.2.0)
 P pkgconfig       2.0.3    2019-09-22 [?] CRAN (R 4.2.0)
 P plyr          * 1.8.8    2022-11-11 [?] CRAN (R 4.2.0)
 P promises        1.2.0.1  2021-02-11 [?] CRAN (R 4.2.0)
 P proxy           0.4-27   2022-06-09 [?] CRAN (R 4.2.0)
 P purrr         * 1.0.1    2023-01-10 [?] CRAN (R 4.2.0)
 P R6              2.5.1    2021-08-19 [?] CRAN (R 4.2.0)
 P ragg            1.2.5    2023-01-12 [?] CRAN (R 4.2.0)
 P Rcpp            1.0.10   2023-01-22 [?] CRAN (R 4.2.0)
 P readr         * 2.1.3    2022-10-01 [?] CRAN (R 4.2.0)
 P readxl        * 1.3.1    2019-03-13 [?] CRAN (R 4.2.2)
   renv            0.16.0   2022-09-29 [1] CRAN (R 4.2.0)
 P reprex          2.0.2    2022-08-17 [?] CRAN (R 4.2.0)
 P reshape2        1.4.4    2020-04-09 [?] CRAN (R 4.2.0)
 P rlang           1.0.6    2022-09-24 [?] CRAN (R 4.2.0)
 P rprojroot       2.0.3    2022-04-02 [?] CRAN (R 4.2.0)
 P rstatix         0.7.2    2023-02-01 [?] CRAN (R 4.2.0)
 P rstudioapi      0.14     2022-08-22 [?] CRAN (R 4.2.0)
 P RVAideMemoire * 0.9-66   2017-07-10 [?] CRAN (R 4.2.2)
 P rvest           1.0.3    2022-08-19 [?] CRAN (R 4.2.0)
 P s2              1.1.2    2023-01-12 [?] CRAN (R 4.2.0)
 P sass            0.4.5    2023-01-24 [?] CRAN (R 4.2.0)
 P scales          1.2.1    2022-08-20 [?] CRAN (R 4.2.0)
 P seqinr          4.2-23   2022-11-28 [?] CRAN (R 4.2.0)
 P sessioninfo     1.2.2    2021-12-06 [?] CRAN (R 4.2.0)
 P sf            * 1.0-2    2021-07-26 [?] CRAN (R 4.2.2)
 P shiny           1.7.4    2022-12-15 [?] CRAN (R 4.2.0)
 P sp              1.6-0    2023-01-19 [?] CRAN (R 4.2.0)
 P spData          2.2.1    2022-11-15 [?] CRAN (R 4.2.0)
 P spdep           1.2-7    2022-10-01 [?] CRAN (R 4.2.0)
 P stringi         1.7.12   2023-01-11 [?] CRAN (R 4.2.0)
 P stringr       * 1.5.0    2022-12-02 [?] CRAN (R 4.2.0)
 P systemfonts     1.0.4    2022-02-11 [?] CRAN (R 4.2.0)
 P textshaping     0.3.6    2021-10-13 [?] CRAN (R 4.2.0)
 P tibble        * 3.1.8    2022-07-22 [?] CRAN (R 4.2.0)
 P tidyr         * 1.3.0    2023-01-24 [?] CRAN (R 4.2.0)
 P tidyselect      1.2.0    2022-10-10 [?] CRAN (R 4.2.0)
 P tidyverse     * 1.3.1    2021-04-15 [?] CRAN (R 4.2.0)
 P timechange      0.2.0    2023-01-11 [?] CRAN (R 4.2.0)
 P tzdb            0.3.0    2022-03-28 [?] CRAN (R 4.2.0)
 P units           0.8-1    2022-12-10 [?] CRAN (R 4.2.0)
 P utf8            1.2.3    2023-01-31 [?] CRAN (R 4.2.0)
 P vctrs           0.5.2    2023-01-23 [?] CRAN (R 4.2.0)
 P vegan         * 2.4-3    2017-04-07 [?] CRAN (R 4.2.2)
 P withr           2.5.0    2022-03-03 [?] CRAN (R 4.2.0)
 P wk              0.7.1    2022-12-09 [?] CRAN (R 4.2.0)
 P xfun            0.37     2023-01-31 [?] CRAN (R 4.2.0)
 P xml2            1.3.3    2021-11-30 [?] CRAN (R 4.2.0)
 P xtable          1.8-4    2019-04-21 [?] CRAN (R 4.2.0)
 P yaml            2.3.7    2023-01-23 [?] CRAN (R 4.2.0)
 P zip             2.2.2    2022-10-26 [?] CRAN (R 4.2.0)

 [1] /Users/adamsparks/Developer/GitHub/AGMccoy/Phytophthora-sojae-global-pathotype-meta-analysis/renv/library/R-4.2/aarch64-apple-darwin20
 [2] /Users/adamsparks/Developer/GitHub/AGMccoy/Phytophthora-sojae-global-pathotype-meta-analysis/renv/sandbox/R-4.2/aarch64-apple-darwin20/fd29d0b8

 P ── Loaded and on-disk path mismatch.
 ```
