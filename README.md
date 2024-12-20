
<!-- README.md is generated from README.qmd. Please edit that file -->

# Applied Regression <a href='https://educ265.de-barros.com/'><img src='files/icon-512.png' align="right" height="139" /></a>

[EDUC 265 • Winter 2025](https://educ265.de-barros.com/)  
[Andreas de Barros](https://www.de-barros.com/) • School of Education •
University of California, Irvine

------------------------------------------------------------------------

**[Quarto](https://quarto.org/) +
[{targets}](https://docs.ropensci.org/targets/) +
[{renv}](https://rstudio.github.io/renv/) +
[{xaringan}](https://github.com/yihui/xaringan) = magic! 🪄**

------------------------------------------------------------------------

## How to build the site

1.  Install
    [RStudio](https://www.rstudio.com/products/rstudio/download/#download)
    version 2022.07.1 or later since it has a
    [Quarto](https://quarto.org/) installation embedded in it.
    Otherwise, download and install [Quarto](https://quarto.org/)
    separately.
2.  Open `educ265-25.Rproj` to open an [RStudio
    Project](https://r4ds.hadley.nz/workflow-scripts.html#projects).
3.  If it’s not installed already, R *should* try to install the [{renv}
    package](https://rstudio.github.io/renv/) when you open the RStudio
    Project for the first time. If you don’t see a message about package
    installation, install it yourself by running
    `install.packages("renv")` in the R console.
4.  Run `renv::restore()` in the R console to install all the required
    packages for this project.
5.  Run `targets::tar_make()` in the R console to build everything.
6.  🎉 All done! 🎉 The complete website will be in a folder named
    `_site/`.

## {targets} pipeline

I use the [{targets} package](https://docs.ropensci.org/targets/) to
build this site and all its supporting files. The complete pipeline is
defined in [`_targets.R`](_targets.R) and can be run in the R console
with:

``` r
targets::tar_make()
```

The pipeline does several major tasks:

- **Create supporting data files**: The problem sets and examples I use
  throughout the course use many different datasets that come
  prepackaged in R packages, I downloaded from sources online, or that I
  generated myself. To make sure I and my students are using the latest,
  most correct datasets, the functions in [`R/tar_data.R`](R/tar_data.R)
  save and/or generate these datasets prior to building the website.

- **Compress project folders**: To make it easier to distribute problem
  sets and in-class activities to students, I compress all the folders
  in the [`/projects/`](/projects/) folder so that students can download
  and unzip a self-contained RStudio Project as a `.zip` file. These
  targets are [dynamically
  generated](https://books.ropensci.org/targets/dynamic.html) so that
  any new folder that is added to `/projects/` will automatically be
  zipped up when running the pipeline.

  The pipeline [dynamically generates
  targets](https://books.ropensci.org/targets/dynamic.html) for all the
  `.Rmd` files in [`/slides/`](/slides/) and renders them using R
  Markdown rather than Quarto.

  The pipeline then uses
  [{renderthis}](https://jhelvy.github.io/renderthis/) to convert each
  set of HTML slides into PDFs.

  I use LaTeX, PowerPoint and xaringan for my slides. The LaTeX and
  PowerPoint slides are created outside the pipeline.

- **Build Quarto website**: This project is a [Quarto
  website](https://quarto.org/docs/websites/), which compiles and
  stitches together all the `.qmd` files in this project based on the
  settings in [`_quarto.yml`](_quarto.yml). See the [Quarto website
  documentation](https://quarto.org/docs/websites/) for more details.

- **Upload resulting `_site/` folder to my remote server**: Quarto
  places the compiled website in a folder named `/_site/`. I push this
  folder to my a Netlify site, using `quarto publish netlify` in my
  RStudio Terminal. Then, I have a subdomain on my website, whose
  settings point to this Netlify site.

## Acknowledgments

This page is largely inspired by [Andrew
Heiss’s](https://www.andrewheiss.com/) site for his class [Program
Evaluation for Public
Service](https://github.com/andrewheiss/evalf22.classes.andrewheiss.com)
as well as [Matt Blackwell’s](https://www.mattblackwell.org/) site for
his class [Gov 50](https://github.com/mattblackwell/gov50-f23-site/). If
you re-use any of the materials, please respect the licences (see below)
and give credit to original authors.

A huge thanks to my excellent Teaching Assistants [Juan Camilo
Cristancho](https://education.uci.edu/phd-cristancho-j.html) and
[Tiffany Wu](https://wutiffany.com/).

I am grateful for additional help and materials from [David
Blazar](https://education.umd.edu/directory/david-blazar), [Fiona
Burlig](https://www.fionaburlig.com/), [Arja
Dayal](https://steinhardt.nyu.edu/arja-dayal), [Pierre de
Galbert](https://scholar.harvard.edu/pierredegalbert/home), [Alejandro
Ganimian](https://www.alejandroganimian.com/), [Andrew
Ho](https://www.gse.harvard.edu/directory/faculty/andrew-ho), [Justine
Knebelmann](https://sites.google.com/view/justine-knebelmann/home),
[Francisco
Lagos](https://education.umd.edu/student-directory/francisco-lagos),
[Fernanda
Ramirez-Espinoza](https://sites.google.com/site/ramirezespinozafernanda/),
and [Carly Robinson](https://www.carlydrobinson.com/).

## Licenses

**Text and figures:** All prose and images are licensed under Creative
Commons ([CC-BY-NC
4.0](https://creativecommons.org/licenses/by-nc/4.0/))

**Code:** All code is licensed under the [MIT License](LICENSE.md).
