
SDU Biology R Club
==================

Material from monthly meetings of the R Club in Biology at SDU.

## Contents
- [Info for presenters](#presenter-notes)
- [Past meetings](#past-meetings)
  - [2019-03](#2019-03)
  - [2019-02](#2019-02)
  - [2019-01](#2019-01)
  - [2018-12](#2018-12)
  - [2018-11](#2018-11)
  - [2018-10](#2018-10)
- [Ideas for future topics](#topic-ideas)
  - [Statistics / modelling](#statistics)
  - [Data visualization](#data-viz)
  - [Data wrangling](#data-wrangling)
  - [Reproducibility / workflows](#reproducibility)
  - [Spatial](#spatial)
  - [Programming](#programming)
  - [Other](#other)
- [Online resources](#online-resources)
  


## <a name="presenter-notes"></a>Info for presenters

The format for presentations is completely flexible. The only rule is that presentations should be limited to 10 minutes (shorter is fine too), unless a longer time-slot is arranged ahead of time (which is perfectly feasable).

Don't worry about repeating material that was previously covered. The universe of statistics and programming is too vast, and our meetings too short and infrequent, for repetition to be a problem.

If your presentation involves written materials (scripts, slides, etc.), it would be great if they could be archived in this repo. R Markdown documents are an ideal way to host such material, because they allow R scripts, their output, and any associated content to be rendered into a single, nicely-formatted HTML document. See a template for an R Markdown presentation [here](template.Rmd), and the resulting markdown document [here](template.md). Note that it's perfectly fine if you don't have the time or desire to use R Markdown.

## <a name="past-meetings"></a>Past meetings

#### <a name="2019-03"></a>2019-03
- Iris: a simulation problem
- Patrick: working with spatial rasters [[link](2019-03/patrick-rasters.md)]

#### <a name="2019-02"></a>2019-02
- Rita: Let’s Map! How to make a map in R [[link](2019-02/rita-lets-map.md)]
- Patrick: checking assumptions of glm models [[link](2019-02/patrick-glm-diagnostics.md)]
- Simeon: model(comparison) in R [[link](2019-02/simeon-model-comparison.md)]

#### <a name="2019-01"></a>2019-01
- Brian: update on potential courses/training/workshops
- Gesa: plotting confidence intervals for glms [[link](2019-01/gesa-confidence-intervals.md)]
- Patrick: intro to managing projects with [GitHub](https://github.com/)

#### <a name="2018-12"></a>2018-12
- Owen: cluster analysis [[link](2018-12/owen-cluster-analysis.md)]
- Gesa: intro to [Rmarkdown](https://rmarkdown.rstudio.com/)
- Iain: [VSCode](https://code.visualstudio.com/) as an alternative to RStudio
- Iris: intro to [ggplot2](https://ggplot2.tidyverse.org/) (#2)

#### <a name="2018-11"></a>2018-11
- Gesa: using [RStudio Projects](https://support.rstudio.com/hc/en-us/articles/200526207-Using-Projects)
- Lio: text-mining with the [tm package](https://cran.r-project.org/web/packages/tm/index.html) (see also [vignette by Ingo Feinerer](https://cran.r-project.org/web/packages/tm/vignettes/tm.pdf))
- Iain: vectorizing functions
- Rita: intro to the [taxize](https://github.com/ropensci/taxize) package
- Patrick: working with factors using [forcats](https://forcats.tidyverse.org/) [[link](2018-11/patrick-forcats.md)]

#### <a name="2018-10"></a>2018-10
- Gesa: managing naming conflicts with [conflicted](https://conflicted.r-lib.org/)  [[link](2018-10/gesa-package-conflicted.md)]
- Iris: introduction to [ggplot2](https://ggplot2.tidyverse.org/)  (#1)
- Patrick: getting help with a problem on [StackOverflow](https://stackoverflow.com/) [[link](2018-10/patrick-minimal-reproducible-questions.md)]
- Brian: nifty but forgettable functions in base R [[link](2018-10/brian-nifty-but-forgettable.md)]
- Stina: auto-formatting problems in Excel

## <a name="topic-ideas"></a>Ideas for future topics

This list is intended to serve as inspiration for future presenters, but many of the categories may be too broad for a single presentation. For example, instead of presenting on "model validation" broadly, one might present on "model validation for logistic regression models".

### <a name="statistics"></a>Statistics / modelling
- model validation / checking assumptions
- model comparison (e.g. AIC)
- model types
  - general linear models
  - type I vs. II vs. III sums of squares
  - generalized additive models
  - non-linear models (e.g. NLS)
  - mixed models / random effects
  - phylogenetic models
- non-parameteric tests
- dealing with missing data (e.g. imputation)
- manually optimizing likelihood functions
- Bayesian methods

Resources: [Quick-R Statistics](https://www.statmethods.net/stats/index.html)

### <a name="data-viz"></a>Data visualization
- color palettes [[cheat sheet](https://www.nceas.ucsb.edu/~frazier/RSpatialGuides/colorPaletteCheatsheet.pdf), [blog post](https://betterfigures.org/2015/06/23/picking-a-colour-scale-for-scientific-graphics/), [colorspace package](http://colorspace.r-forge.r-project.org/index.html)]
- animation [[gganimate](https://gganimate.com/), [animation](https://cran.r-project.org/web/packages/animation/index.html), [gallery of animations for statistics](https://yihui.name/animation/examples/)]
- putting multiple plots on one page

Resources: [Fundamentals of Data Visualization](https://ourcodingclub.github.io/tutorials/), [R Graphics Cookbook](http://www.cookbook-r.com/Graphs/), [Quick-R Advanced Graphs](https://www.statmethods.net/advgraphs/parameters.html)

### <a name="data-wrangling"></a>Data wrangling
- tidy data principles [[paper by Hadley Wickham](https://www.jstatsoft.org/article/view/v059i10)]
- [tidyverse](https://www.tidyverse.org/) packages
- working with dates/times
- regular expressions [[R doc](https://stat.ethz.ch/R-manual/R-devel/library/base/html/regex.html)]

Resources: [Quick-R Data Management](https://www.statmethods.net/management/index.html)


### <a name="reproducibility"></a>Reproducibility / workflows
- Git / GitHub
- Rmarkdown [[Intro by RStudio](https://rmarkdown.rstudio.com/lesson-1.html)]
- using R in the cloud

Resources: [Cran Task View: Reproducible Research](https://cran.r-project.org/web/views/ReproducibleResearch.html)


### <a name="spatial"></a>Spatial
- making maps
- working with shapefiles
- packages rgeos, rgdal, raster, sp, sf, ...

Resources: [CRAN Task View: Analysis of Spatial Data](https://cran.r-project.org/web/views/Spatial.html), [Geocomputation with R by Lovelace et al.](https://geocompr.robinlovelace.net/)


### <a name="programming"></a>Programming
- writing custom functions
- control flow functions (if, for, while, ifelse, switch) [[R doc](https://stat.ethz.ch/R-manual/R-devel/library/base/html/Control.html), [Advanced-R chapter](https://adv-r.hadley.nz/control-flow.html)]
- debugging code
- code style [[Google's style guide](https://google.github.io/styleguide/Rguide.xml), [Advanced-R chapter](http://adv-r.had.co.nz/Style.html)]
- non-standard evaluation [[Advanced-R chapter](http://adv-r.had.co.nz/Computing-on-the-language.html)]


### <a name="other"></a>Other
- scraping data off the web [[rvest package](https://blog.rstudio.com/2014/11/24/rvest-easy-web-scraping-with-r/)]
- bioinformatics applications
- image processing
- parallel processing
- writing R packages [[post by Hilary Parker](https://hilaryparker.com/2014/04/29/writing-an-r-package-from-scratch/), [R Packages by Hadley Wickham](http://r-pkgs.had.co.nz/)]


## <a name="online-resources"></a>Online resources
- [Advanced R](https://adv-r.hadley.nz/) by Hadley Whickham
- [Quick-R](https://www.statmethods.net/index.html) by DataCamp
- [R for Data Science](https://r4ds.had.co.nz/) by Grolemund & Wickham
- [R Programming for Data Science](https://bookdown.org/rdpeng/rprogdatascience/) by Roger Peng
- [Coding Club Tutorials](https://ourcodingclub.github.io/tutorials/)
- [RStudio Cheat Sheets](https://www.rstudio.com/resources/cheatsheets/)
- [Fundamentals of Data Visualization](https://serialmentor.com/dataviz/) by Claus Wilke
- [UBC Stat545 course materials](http://stat545.com/topics.html) by Jenny Bryan et al.
