# R packages
# 1. Debugging tips:
## How should I deal with “package 'xxx' is not available (for R version x.y.z)” warning?
1. You can't spell
The first thing to test is have you spelled the name of the package correctly? Package names are case sensitive in R.
2. You didn't look in the right repository. Next, you should check to see if the package is available. Type:
setRepositories()
3. The package is not in the repositories you selected
4. You don't want a package
Perhaps you don't really want a package. It is common to be confused about the difference between a package and a library, or a package and a dataset.

    A package is a standardized collection of material extending R, e.g. providing code, data, or documentation. A library is a place (directory) where R knows to find packages it can use

To see available datasets, type: data()
5. R or Bioconductor is out of date
It may have a dependency on a more recent version of R (or one of the packages that it imports/depends upon does). 
Consider updating your R installation to the current version. On Windows, this is most easily done via the installr package.
library(installr)
updateR()

Of course, you may need to install.packages("installr") first.
Equivalently for Bioconductor packages, you may need to update your Bioconductor installation.
source("http://bioconductor.org/biocLite.R")
biocLite("BiocUpgrade")

