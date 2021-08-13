## Installing PHRAPL via conda
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
conda install -c r r-rgl
conda install -c r r-rcolorbrewer
conda install -c conda-forge r-binom
conda install -c conda-forge r-diagram
```
* Try typing `which R` to make sure it's the version you just installed with conda.
* Start R by typing `R`
* And then install PHRAPL from within R:
`devtools::install_github("bomeara/phrapl")`
