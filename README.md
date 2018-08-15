# R packages
# 1. Debugging tips:
## How should I deal with “package 'xxx' is not available (for R version x.y.z)” warning?
1. You can't spell
The first thing to test is have you spelled the name of the package correctly? Package names are case sensitive in R.
2. You didn't look in the right repository
setRepositories()
