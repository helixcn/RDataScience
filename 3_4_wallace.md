# Wallace
Jamie Kass, Matt Aiello-Lammens  



<div>
<object data="3_4_assets/Wallace_Intro.pdf" type="application/pdf" width="100%" height="650px"> 
  <p>It appears you don't have a PDF plugin for this browser.
   No biggie... you can <a href="3_4_assets/Wallace_Intro.pdf">click here to
  download the PDF file.</a></p>  
 </object>
 </div>
 
 <p><a href="3_4_assets/Wallace_Intro.pdf">Download the PDF of the presentation</a></p>  

[<i class="fa fa-file-code-o fa-3x" aria-hidden="true"></i> The R Script associated with this page is available here](3_4_wallace.R).  Download this file and open it (or copy-paste into a new script) with RStudio so you can follow along.  

# *Wallace*

*Wallace* is a modular platform for reproducible modeling of species niches and distributions, written in R with the web app development package `shiny`. The application guides users through a complete analysis, from the acquisition of data to visualizing model predictions on an interactive map, thus bundling complex workflows into a single, streamlined interface.

*Wallace* is currently available via Github using `devtools::install_github('wallaceEcoMod/wallace')`. All development for the project occurs in this repository. You can get *Wallace* up and running with a few lines of code.


```r
# if you do not have devtools installed, install it first
install.packages("devtools", repos = "http://cran.us.r-project.org")
# install wallace from github
devtools::install_github("wallaceEcoMod/wallace")
# load wallace
library(wallace)
# run the user interface
wallace()
```

While the above will get you going, if you want to use the *Maxent* component, you'll have to follow a few more steps.
These steps are listed in the documentation at the bottom (i.e., the `README.md` file) of [this page](https://github.com/wallaceEcoMod/wallace).

# *Wallace* is **Modular**

Developers can (and are encouraged to) contribute new methods to *Wallace* by submitting pull requests for new modules. This feature is key to the concept of *Wallace*, which was built for community expansion.

The way developers can do this may change in future versions, but we will provide a simple example of adding a module in the current framework.

# Architecture of *Wallace*

*Wallace* has 8 "components" that represent key steps of a niche/distributional modeling analysis. Within each component, there are a number of "modules", which represent methodological options for that particular step. For example, the sixth component **Model** has modules ***BIOCLIM*** and ***Maxent***.

For all `shiny` apps, there are two main parts: "ui" and "server". The UI part generates all the controls and displays of the user interface, while the server part runs all the functions in the background.

Within the `inst/shiny` folder, *Wallace* has a script for each part: `server.R` and `ui.R`. In addition, there are scripts that contain the modules for each component in `/modules`. These are `source()`ed in `server.R`. Adding a new module involves making edits to each of these scripts, as you'll need to add not only the functionality, but the buttons, check boxes, maps, tables, etc. that the user interacts with and views.


# Example workflow

Before getting into how to expand *Wallace*, let's work our way through an example workflow. If you have successfully installed *Wallace* then please follow along, or feel free to ignore us and try things out yourself. If you haven't been able to get the install to work, then follow us as we go through it in front, and come talk with Jamie or Matt after the workshop. We'll try to help trouble shoot your install problems. 

# Using the resulting `*.Rmd` file to expand your modeling

The last step of a Wallace workflow is downloading the session information. There are multiple formats available, but the [RMarkdown](http://rmarkdown.rstudio.com/) format (i.e., `*.Rmd`) is likely the most useful. This format allows you to re-run, share, and modify the R code from your session. 

## Using `gam`s as a modeling method

As an example of the utility of the `*.Rmd` format, let's imagine that you want to use a **generalized addative model** as an additional SDM approach. Looking through the `*.Rmd` file, we can find the **code chunk** (using the parlance of RMarkdown) where we run our SDM, and add a new section of text and code chunk to run a GAM.

# Let's add GAMs to *Wallace*

Say that for your particular research needs, you'd like use GAMs frequently, and through the *Wallace* GUI, in addition to the models available in *Wallace*, and possibly compare the results.

You'll be working in `mods_comp6.R`, `server.R`, and `ui.R`. Let's start with the functionality for the UI.

## UI development

To start, you'll need to imagine what the user will need to input to *Wallace* in order to have your module work. In the case of GAMs (the simplest case), perhaps you envision users entering the variables that go into the model and specifying a smoothing parameter to apply to all variables.







