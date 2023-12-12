## Part 1D:

[Here](https://github.com/njudd/ggrain) is the link to where the original R package came from.

[Here](https://jhu-statprogramming-fall-2023.github.io/biostat840-project3-pkgdown-<nora-elhaissouni>)

These are the 5 things I customized for the pkgdown website:
bootswatch: sandstone - this customization made the theme sandstone which is warmer and neutral colors to the different buttons and navigations of the website
bslib:
  bg: "#F5F5F5" - a light grey shade for the website background
  fg: "#333333" - dark grey main text
  primary: "#007BFF" - blue color for the main buttons and packages/functions
  base_font: {google: "Roboto"} - this customized the text font to Roboto retrived from google fonts
  code-bg: "#FFFFFF" - code blocks background color is white (for descrubing the functions in the text not in code blocks)
  theme: solarized-light - overall theme color palette set

Original author of the package: Listed in the citations
Example Analysis Author: Nora Elhaissouni
Exported functions and examples are below:


<img src="https://github.com/jorvlan/open-visualizations/blob/master/R/package_figures/Rplot03.png" width="200" height="190" align="right"/>

[![R-CMD-check](https://github.com/njudd/ggrain/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/njudd/ggrain/actions/workflows/R-CMD-check.yaml)
[![Bugs](https://img.shields.io/github/issues/njudd/ggrain/bug?label=Bugs&logo=github&logoColor=%23FFF&color=brightgreen)](https://github.com/njudd/ggrain/issues?q=is%3Aopen+is%3Aissue)
[![CRAN_Release_Badge](http://www.r-pkg.org/badges/version-ago/ggrain)](https://CRAN.R-project.org/package=ggrain)
[![CRAN_Download_Badge](http://cranlogs.r-pkg.org/badges/grand-total/ggrain)](https://CRAN.R-project.org/package=ggrain)
[![](http://cranlogs.r-pkg.org/badges/ggrain)](https://cran.r-project.org/package=ggrain)
[![Vignette](https://img.shields.io/badge/Vignette-ggrain-orange.svg?colorB=E91E63)](https://www.njudd.com/raincloud-ggrain/)
[![](https://img.shields.io/badge/Raincloudplots-shinyapps.io-blue?style=flat&labelColor=white&logo=RStudio&logoColor=blue)](https://lcdlab.shinyapps.io/raincloudplots-shiny/)
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

There are two ways to install this package.

1. Download the [CRAN](https://CRAN.R-project.org/package=ggrain) version  
```r
install.packages("ggrain")

library(ggrain)
```

2. Download through [GitHub](https://github.com/njudd/ggrain)
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

![img](https://raw.githubusercontent.com/njudd/ggrain/main/inst/git_pics/time_group_cov_vin.png)

### Contributions / Issues

We warmly welcome all contributions. 
You can open an issue or make a pull request if you would like to add something new!

### Citation

[`ggrain`](https://github.com/njudd/ggrain) was developed by Nicholas Judd, Jordy van Langen, Micah Allen, and Rogier Kievit. 

<pre>
- Judd, N., van Langen, J., Allen, M., & Kievit, R.A.
    <i>ggrain: A Rainclouds Geom for 'ggplot2'.</i>
    R package version 0.0.3.
    <b>CRAN</b> 2023,
    <a href="https://CRAN.R-project.org/package=ggrain">https://CRAN.R-project.org/package=ggrain</a>
</pre>

### Funding
<img src="https://github.com/njudd/ggrain/blob/main/inst/git_pics/nwo_openscience.jpg" width="150" height="160" align="right"/>

In 2021, NWO (Dutch research council) announced their inaugural [NWO Open Science Fund](https://www.nwo.nl/en/researchprogrammes/open-science/open-science-fund). The Open Science Fund aims to support researchers to develop, test and implement innovative ways of making research open, accessible, transparent and reusable, covering the whole range of Open Science. The Raincloud plots team was awarded this fantastic initiative and is specifically working on:

- Creating the [`ggrain`](https://github.com/njudd/ggrain) R-package
- Creating an interactive R Shiny application [`raincloudplots`](https://lcdlab.shinyapps.io/raincloudplots-shiny/)
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

There are now ***4*** ways in which you can use our Raincloud Plots tools: 
- through a series of specific easy to modify scripts [https://github.com/RainCloudPlots/RainCloudPlots](https://github.com/RainCloudPlots/RainCloudPlots)
- through our initial [`raincloudplots`](https://github.com/jorvlan/raincloudplots) package
- through the newest R-package [`ggrain`](https://github.com/njudd/ggrain)
- through our R Shiny application: [`raincloudplots`](https://lcdlab.shinyapps.io/raincloudplots-shiny/)
