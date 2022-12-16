[![R-CMD-check](https://github.com/njudd/ggrain/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/njudd/ggrain/actions/workflows/R-CMD-check.yaml)
[![CRAN_Release_Badge](http://www.r-pkg.org/badges/version-ago/ggrain)](https://CRAN.R-project.org/package=ggrain)
[![CRAN_Download_Badge](http://cranlogs.r-pkg.org/badges/grand-total/ggrain)](https://CRAN.R-project.org/package=ggrain)
[![](http://cranlogs.r-pkg.org/badges/ggrain)](https://cran.r-project.org/package=ggrain)
[![](http://cranlogs.r-pkg.org/badges/last-week/ggrain)](https://cran.r-project.org/package=ggrain)
[![Vignette](https://img.shields.io/badge/Vignette-ggrain-orange.svg?colorB=E91E63)](https://www.njudd.com/raincloud-ggrain/)
<!---[![License: ]()](https://github.com/njudd/ggrain/LICENSE)--->

# `ggrain` - [Raincloud Plots](https://wellcomeopenresearch.org/articles/4-63/v2)

`ggrain` is an R-package that allows you to create Raincloud plots - following the 'Grammar of Graphics' (i.e., ggplot2) - that are: 

- Highly customizable
- Connect longitudinal observations
- Handles Likert data
- Allows mapping of a covariate.
	
### Example 

```r
ggplot(iris, aes(x = 1, y = Sepal.Length)) +
  geom_rain()
```

### Installation

```r
if (!require(remotes)) {
    install.packages("remotes")
}
remotes::install_github('njudd/ggrain')

library(ggrain)
```

###  Simple examples

1.  Raincloud per group

	```r
	ggplot(iris, aes(x = Species, y = Sepal.Length, fill = 	Species)) +
		geom_rain(rain.side = 'l')
	```

2.  Different groups overlapped

	```r
	ggplot(iris, aes(x = 1, y = Sepal.Length, fill = Species)) +
		geom_rain(alpha = .5)
	```


![img](https://raw.githubusercontent.com/njudd/ggrain/main/inst/git_pics/basic_rain.png)

### Vignette
For a complete overview of `ggrain` such as a 2-by-2 raincloud plot or multiple repeated measures, please see our [Vignette](https://www.njudd.com/raincloud-ggrain/).

### `ggrain` specific features

`geom_rain` is a combination of 4 different ggplot2 geom's (i.e., point, line, boxplot & violin).

- `id.long.var`: a grouping variable to connect the lines by
- `cov`: a covariate to remap the color of the points
- `Likert`: `True` or `False` response which adds y jittering
- `rain.side`: Which side to display the rainclouds: 'l' for left, 'r' for right and 'f' for flanking

Specific geom arguments can be passed with a list to any of the 4 geom's with the argument `{point/line/boxplot/violin}.args`. For a list of arguments that can be passed see the help files of the respective geom's (e.g., `?gghalves::geom_half_violin`).

Position-related arguments (e.g., jittering, nudging & width) can be passed with `{point/line/boxplot/violin}.args.pos`, see the help file of `?geom_rain` for defaults

![img](https://raw.githubusercontent.com/njudd/ggrain/main/inst/git_pics/time_group_cov.png)

### Contributions

We warmly welcome all contributions. 
You can open an issue or make a pull request if you would like to add something new!


### Citation

<pre>
- Judd, Nicholas, van Langen, Jordy, & Kievit, Rogier.
    ggrain: a ggplot2 extension package to create Raincloud Plots in R
    <b>GitHub</b> 2022, 
    <a href="https://github.com/njudd/ggrain">https://github.com/njudd/ggrain</a>
</pre>

### Funding
<img src="https://github.com/njudd/ggrain/blob/main/inst/git_pics/nwo_openscience.jpg" width="150" height="160" align="right"/>

In 2021, NWO (Dutch research council) announced their inaugural [NWO Open Science Fund](https://www.nwo.nl/en/researchprogrammes/open-science/open-science-fund). The Open Science Fund aims to support researchers to develop, test and implement innovative ways of making research open, accessible, transparent and reusable, covering the whole range of Open Science. The Raincloud plots team was awarded this fantastic initiative and is specifically working on:

- Creating the `ggrain` R-package
- Creating a ShinyApp Raincloudplots
- Integrating Raincloudplots in [JASP Statistics](https://jasp-stats.org)
- Organzing [globally accessible, online workshops](https://github.com/jorvlan/raincloudplots-workshops) to help people create raincloudplots and improve their data visualizations in general.

You can read more about our awarded project here: https://www.nwo.nl/en/projects/203001011 or you can watch the online webinar hosted by NWO about our project: [![Webinar Open Science series S1E2: Open tools for data enrichment and visualization](https://github.com/njudd/ggrain/blob/main/inst/git_pics/raincloudplots_NWO_webinar.png)](https://youtu.be/Kvcyh_9KSbw?t=1910 "Webinar Open Science series S1E2: Open tools for data enrichment and visualization")


### Raincloud Plots 

**Paper**
<br>
<pre>
- Allen, M., Poggiali, D., Whitaker, K., Marshall, T. R., van Langen, J., & Kievit, R. A.
    Raincloud plots: a multi-platform tool for robust data visualization [version 2; peer review: 2 approved] 
    <b>Wellcome Open Research</b> 2021, 4:63. <a href="https://doi.org/10.12688/wellcomeopenres.15191.2">https://doi.org/10.12688/wellcomeopenres.15191.2</a>
</pre>

There are now ***3*** ways to make it rain in R: through a series of specific easy to modify scripts, through our initial `raincloudplots` package, and now through the newest R-package `ggrain`. 

Raincloud plots were created and developed by Micah Allen, Davide Poggiali, Kirstie Whitaker, Tom Rhys Marshall, Jordy van Langen and Rogier Kievit.

*Across scientific disciplines, there is a rapidly growing recognition of the need for more statistically robust, transparent approaches to data visualization. Complementary to this, many scientists have called for plotting tools that accurately and transparently convey key aspects of statistical effects and raw data with minimal distortion. Previously common approaches, such as plotting conditional mean or median barplots together with error-bars have been criticized for distorting effect size, hiding underlying patterns in the raw data, and obscuring the assumptions upon which the most commonly used statistical tests are based. We describe a data visualization approach which overcomes these issues, providing maximal statistical information while preserving the desired ‘inference at a glance’ nature of barplots and other similar visualization devices. These “raincloud plots” can visualize raw data, probability density, and key summary statistics such as median, mean, and relevant confidence intervals in an appealing and flexible format with minimal redundancy. We created and shared our open-source code for raincloudplots implementation in R, Python and Matlab* 
<a href="https://github.com/RainCloudPlots/RainCloudPlots">https://github.com/RainCloudPlots/RainCloudPlots</a>.

<img src="https://github.com/njudd/ggrain/blob/inst/git_pics/rainclouds_highres.png" width="150" height="160" align="right"/>

*In addition to this step-by-step tutorial, we have created our first [`raincloudplots`](https://github.com/jorvlan/raincloudplots) R-package. This package is tailored towards easy visualization of grouped and repeated measures data. Moreover, it also provides individually linked repeated measures visualizations, which add detail and richness to a multitude of within-subject designs. Here, we have chosen to depict the two most common repeated measures designs: 1 * 1 and 2 * 2. Basically, it wraps complex arguments into 1 single data and plotting function that does all the magic for you.*


