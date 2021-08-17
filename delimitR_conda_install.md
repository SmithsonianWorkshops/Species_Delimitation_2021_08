## Installing delimitR via conda
* GitHub page: https://github.com/meganlsmith/delimitR

### Installing fastsimcoal2
* Download the version for your operating system e.g.
 `wget http://cmpg.unibe.ch/software/fastsimcoal26/downloads/fsc26_linux64.zip`

* Unzip and then make executable with `chmod +x fsc26`
  
* See our conda_instructions.md (https://github.com/SmithsonianWorkshops/Species_Delimitation_2021_08/blob/main/conda_instructions.md) and create an environment just for delimitR.
* If you are working on a linux system, there is a conda environment yml file here: https://github.com/SmithsonianWorkshops/Species_Delimitation_2021_08/blob/main/conda_environment_yml_files/delimitR_linux.yml (you can use this file to build a new environment with all dependencies with `conda env create --file delimitR_linux.yml`
* This will avoid any dependency conflict with any other R installations you have.
* Next, install the necessary dependencies via conda:
```
conda install -c r r 
conda install python=2.7
conda install -c conda-forge r-devtools
conda install -c conda-forge r-stringi
conda install -c conda-forge r-stringr
conda install -c conda-forge r-knitr
conda install -c conda-forge r-rsqlite
conda install -c r r-dplyr
conda install -c conda-forge r-readr
conda install -c bioconda r-rematch2
conda install -c r r-rmarkdown
conda install -c conda-forge r-sqldf
conda install -c r r-testthat
conda install -c conda-forge r-tibble
conda install -c conda-forge r-vroom
conda install -c conda-forge r-waldo
conda install -c conda-forge r-ranger
conda install -c r r-foreach
conda install -c r r-doparallel
conda install -c conda-forge r-matrixstats

```
* Then download the delimitR code:
`git clone https://github.com/meganlsmith/delimitR.git`
* Unpack the tar.gz file
* Set your working directory to the directory above the delimitR directory that was created when you unpacked the source code.
* Try typing `which R` to make sure it's the version you just installed with conda.
* Start R by typing `R`
* Install one more dependency not available via conda: `install.packages("abcrf")`
* And then install delimitR from within R:
```
devtools::install('delimitR', dependencies = TRUE)
```
