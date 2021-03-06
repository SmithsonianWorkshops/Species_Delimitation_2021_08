## Installing PHRAPL via conda
* Here are the official instructions: https://phrapl.github.io/Content/1.Installation.html#for-macos
* Note that the above instructinos require root privileges. 
* Below, we have tried to build an environment (for Macs) for which you do not have to use sudo:

### Mac-specific instructions

Create a Conda environment from a file we posted here to this GitHub repo:

`conda env create -f https://raw.githubusercontent.com/SmithsonianWorkshops/Species_Delimitation_2021_08/main/conda_environment_yml_files/OX_env_phrapl.yml`

Activate this environment:

`conda activate OX_env_phrapl`

Enter R to complete the last few installation steps:

`R`

In R, run these commands:

```R
library(devtools)
devtools::install_url("https://cran.r-project.org/src/contrib/Archive/rPython/rPython_0.0-6.tar.gz", upgrade=FALSE)
devtools::install_url("https://cran.r-project.org/src/contrib/Archive/P2C2M/P2C2M_0.7.6.tar.gz", upgrade=FALSE)
devtools::install_github("bomeara/phrapl")
```

* The below may work on other systems:
* First, see our conda_instructions.md (https://github.com/SmithsonianWorkshops/Species_Delimitation_2021_08/blob/main/conda_instructions.md) and create an environment just for PHRAPL. 
* This will avoid any dependency conflict with any other R installations you have.
* Next, install the necessary dependencies via conda:
```
conda install -c r r
conda install -c conda-forge r-devtools
conda install -c conda-forge r-ape
conda install -c conda-forge r-partitions
conda install -c r r-lattice
conda install -c conda-forge r-polynom
conda install -c conda-forge r-gmp
conda install -c r r-rgenoud
conda install -c conda-forge parallel
conda install -c conda-forge r-optimx
conda install -c r r-igraph
conda install -c conda-forge r-numderiv
conda install -c conda-forge r-nloptr
conda install -c conda-forge r-matrix
conda install -c r r-rcolorbrewer
conda install -c conda-forge r-binom
conda install -c conda-forge r-diagram
conda install -c r r-rjsonio
conda install -c conda-forge r-stringr
conda install -c conda-forge r-ggplot2
conda install python=2.7
```
* Download these libraries separately and unzip:
wget https://github.com/ariadnamorales/phrapl-manual/blob/master/dependencies/rPython_0.0-6.tar.gz
wget https://github.com/ariadnamorales/phrapl-manual/blob/master/dependencies/P2C2M_0.7.6.tar.gz
* If `wget` doesn't work on your system, download them directly from the GitHub site by clicking.

* Try typing `which R` to make sure it's the version you just installed with conda.
* Start R by typing `R`
* Install rPython:
`install.packages("rPython", repos=NULL)`
* Install P2C2M:
`install.packages("P2C2M", repos=NULL)`
* And then install PHRAPL from within R:
`devtools::install_github("bomeara/phrapl")`

