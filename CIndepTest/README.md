## I. Description
Testing for conditional independence between the truncation and failure times can be impletemented by using the package, which is written in the programming language R <https://www.r-project.org>. 


## II. Installation
Download the zip file CIndepTest_0.0.999.zip	and install it on your R. The way to install the package from a local zip file in R is well described at http://outmodedbonsai.sourceforge.net/InstallingLocalRPackages.html

## III. Implementation
The following information must be inputted into the main function 'cindep.test' of the 'CIndepTest' package.

* left-truncated time (w)
* Failure time (y)
* Censoring indicator (d = 1 for event; d = 0 for being censored)
* Matrix for Covariates (x)

Note that y should be greater than w; otherwise, the function throws an error.


## IV. Example
Here, the data set 'abortion' from the package 'etm is used as an example

```r
library(CIndepTest) # Please run after installing the package from the zip file

install.packages("etm") # to bring the example
library(etm) 
data("abortion") # data example: 'abortion'
head(abortion)

subdat <- abortion[abortion[,5]!=2,]
w <- subdat[, 2] # left-truncated time
y <- subdat[, 3] # failure time
d <- ifelse(subdat[, 5] == 1, 0, 1) # censoring indicator
x <- subdat[, 4] # covariate

res <- cindep.test(w, y, d, x, B = 500)
res
```
