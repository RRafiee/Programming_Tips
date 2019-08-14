# R packages
# Debugging tips:
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

6. The package is out of date

7. There is no Windows/OS X/Linux binary

8. The package is on github/Bitbucket/Gitorious

9. There is no source version of the package

10. The package is in a non-standard repository


# Error in mcfork() or R multicore mcfork(): Unable to fork: Cannot allocate memory
# Debugging tips:

The issue might be exactly what the error message suggests: there isn't enough memory to fork and create parallel processes.

R essentially needs to create a copy of everything that's in memory for each individual process (to my knowledge it doesn't utilize shared memory). If you are already using 51% of your RAM with a single process, then you don't have enough memory to create a second process since that would required 102% of your RAM in total.

Try:
1) Using fewer cores - If you were trying to use 4 cores, it's possible you have enough RAM to support 3 parallel threads, but not 4. registerDoMC(2), for example, will set the number of parallel threads to 2 (if you are using the doMC parallel backend).

2) Using less memory - without seeing the rest of your code, it's hard to suggest ways to accomplish this. One thing that might help is figuring out which R objects are taking up all the memory (Determining memory usage of objects using object.size() or memory.profile()) and then removing any objects from memory that you don't need (rm(my_big_object))

3) Adding more RAM - if all else fails, throw hardware at it so you have more capacity.
    
4) Sticking to single threading - multithreaded processing in R is a tradeoff of CPU and memory. It sounds like in this case you may not have enough memory to support the CPU power you have, so the best course of action might be to just stick to a single core.

# R Installation Problem on Windows 10 64 bit
## Rstudio can't launch on windows 10. Just a blank screen!
Check the version of R you have installed on Windows. Try not to use the follwoing version: RStudio-1.2.1335 (129,985KB)

I have used this version which is properly working: RStudio-1.3.322 (163,236KB)

