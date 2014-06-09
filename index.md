---
title       : Shiny App
subtitle    : Presentation of Shiny Application
author      : Created by andonman
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
---

## About the Application

This application ilustrates estimation of the mean squared error.  

In statistics, the mean squared error (MSE) of an estimator measures the average of the squares of the "errors", that is, the difference between the estimator and what is estimated.



## Galton's Data

This application uses the data originally used by Francis Galton in 1885.

Galton was a statistician who invented the term and concepts of regression and correlation, founded the journal Biometrika, and was the cousin of Charles Darwin.

You may need to run install.packages("UsingR") if the UsingR library is not installed.


```r
library(UsingR)
```

```
## Loading required package: MASS
```


--- .class #id 


```r
data(galton)
head(galton, 3)
```

```
##   child parent
## 1  61.7   70.5
## 2  61.7   68.5
## 3  61.7   65.5
```

```r
summary(galton)
```

```
##      child          parent    
##  Min.   :61.7   Min.   :64.0  
##  1st Qu.:66.2   1st Qu.:67.5  
##  Median :68.2   Median :68.5  
##  Mean   :68.1   Mean   :68.3  
##  3rd Qu.:70.2   3rd Qu.:69.5  
##  Max.   :73.7   Max.   :73.0
```


--- .class #id 

# The least squares estimate is the empirical mean


```r
hist(galton$child, col = "blue", breaks = 100)
meanChild <- mean(galton$child)
lines(rep(meanChild, 100), seq(0, 150, length = 100), col = "red", lwd = 5)
```

![plot of chunk unnamed-chunk-3](assets/fig/unnamed-chunk-3.png) 




--- .class #id 

## Summary

This application supports interaction from the user, which can be used  by the user to discover what value of mu minimizes the sum of the squared deviations.


```r
shinyServer(function(input, output) {
    output$newHist <- renderPlot({
        hist(galton$child, xlab = "child height", col = "lightblue", main = "Histogram")
        mu <- input$mu
        lines(c(mu, mu), c(0, 200), col = "red", lwd = 5)
        mse <- mean((galton$child - mu)^2)
        text(63, 150, paste("mu = ", mu))
        text(63, 140, paste("MSE = ", round(mse, 2)))
    })
})
```



The user's input is taken from the slider, which the application uses inside ui.R file.
Every changes made by the user, are visible almost immidiately.



```r
sliderInput("mu", "Guess at the mu", value = 70, min = 60, max = 80, step = 0.05)
```



