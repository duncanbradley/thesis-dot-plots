# Chapter 4: Magnitude Judgements Are Influenced by Data Points’ Relative Positions Within Axis Limits

* Data are in the `data` folder (this also contains the script for anonymising original data files)
* Analysis code is in the `dot-plots-axes.qmd` (quarto) file

## Instructions for Using Docker To Generate the Manuscript Within a Fully-Reproducible Environment

This repository provides resources for re-creating the computational environment (R version, package versions) used for all data wrangling, data visualization, statistical modelling, and reporting. This will generate a fully interactive RStudio session, which will be running from a Docker container.

1. Download [Docker Desktop](https://www.docker.com) and launch it
2. Clone this repository to your local machine
3. Use the command line to navigate to the repository
4. Type `docker build -t thesis-dot-plots .` (where `thesis-dot-plots` is the repository name). This builds the Docker image.
5. Type `docker run --rm -p 8787:8787 -e PASSWORD=password thesis-dot-plots` to launch the Docker container.
6. In your browser's address bar, type `localhost:8787`
7. Enter `rstudio` as the username and `password` as the password. 
8. Open `dot-plots-axes.qmd` and press Render to generate `dot-plots-axes.pdf`

Note: Computationally intensive statistical models have been saved in `dot-plots-axes_cache`. To speed-up rendering, these cached models are loaded instead of executing the code that generated them. To generate models from scratch, change the `eval_models` parameter in line 7 to `true`.

In case of a Sementation Fault error, add the following code to the script and then run `rmarkdown::render("dot-plot-axes.qmd", output_file = "dot-plot-axes.pdf")` in the RStudio console

```
knitr::opts_chunk$set(
  echo = FALSE, include = FALSE, warning = FALSE, message = FALSE
)
```
