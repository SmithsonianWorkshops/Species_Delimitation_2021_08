## Installing the software for the Machine Learning tutorial by Shahan Derkarabetian via conda
* First, see our conda_instructions.md (https://github.com/SmithsonianWorkshops/Species_Delimitation_2021_08/blob/main/conda_instructions.md) and create an environment just for this set of tools.
* This will avoid any dependency conflict with any other R installations you have.
* Next, install the necessary dependencies via conda:
  
```
conda install -c conda-forge r-base=3.5.1
conda install -c bioconda r-adegenet
conda install -c conda-forge tsne
conda install -c conda-forge r-mclust
conda install -c conda-forge r-factoextra
conda install -c bioconda r-classdiscovery
```
* Optional: you can also install a new copy of R Studio in your conda environment with:
```
conda install -c r rstudio 
rstudio &
```
* If still in the terminal, try typing `which R` to make sure it's the version you just installed with conda and start R by typing `R`
* Whether in R Studio or on the terminal, install delimitR from within R:
```
install.packages("PCDimension")
```
