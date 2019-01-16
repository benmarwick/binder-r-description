# Specifying an R environment by having a DESCRIPTION file

If we specify R package dependencies in the DESCRIPTION, they will be installed and available to us in the RStudio in binder. 

Here we are testing if we can use only the DESCRIPTION file to deploy Binder, and including some complex packages such as `sf` and the `tidyverse` in the `Imports` field. We are also using some GitHub-only packages via the `Remotes` field in the DESCRIPTION file.  

The result is that `sf` fails to install, and we do not get the pkgs listed in the `Remotes` field. So we really cannot rely on the DESCRIPTION file to deply the Binder instance. We need to have an `install.R` with code to install from GitHub, and an `apt.txt` to install the linux libraries needed for complex pkgs like `sf`

RStudio: [![Binder](http://mybinder.org/badge.svg)](http://beta.mybinder.org/v2/gh/benmarwick/binder-r-description/master?urlpath=rstudio)

Binder supports using R and RStudio, with libraries pinned to a specific snapshot on [MRAN](https://mran.microsoft.com/documents/rro/reproducibility).

We are not using a `runtime.txt` here, so Binder will use a 2-day old snapshot of MRAN.

If we specify a `runtime.txt` file that is formatted like:

```
r-<YYYY>-<MM>-<DD>
```

where YYYY-MM-DD it will use the MRAN snapshot of that day for setting up the R runtime.

Both [RStudio](https://www.rstudio.com/) and [IRKernel](https://irkernel.github.io/)
are installed by default, so we can use either the Jupyter notebook interface or
the RStudio interface.
