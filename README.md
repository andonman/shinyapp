# Getting Started Guide
ShinyApps is a platform as a service (PaaS) for hosting Shiny applications.  This guide should help you get started 
with ShinyApps allowing you to create your online account, and deploy your first Shiny application to the cloud.


## Requirements

To get started with ShinyApps you will need:

- An R development environment
- The latest version of the [`devtools` package](https://github.com/hadley/devtools)
- The [`shinyapps` package](https://github.com/rstudio/shinyapps) from GitHub 
- A working shiny application on your machine
- Windows: RTools for building packages
- Mac OSX: XCode Command Line Tools for building packages

### Installing the devtools package

:warning: ShinyApps makes uses of the latest improvements to the `devtools` package, you **must** update `devtools` to 
version 1.4 or later.

Install `devtools` from CRAN:

    install.packages('devtools')

        (restart your R session)

	### Installing the shinyapps package

	The `shinyapps` package is used to deploy Shiny applications to the ShinyApps service. The package can only be installed 
	from GitHub at this time.

	Install the `shinyapps` package using `devtools`:

	    devtools::install_github('rstudio/shinyapps')

	    After the `shinyapps` package has been installed, load it into your R session:

	        library(shinyapps)

