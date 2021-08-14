## Installing delimitR via conda
* GitHub page: https://github.com/meganlsmith/delimitR

### Installing fastsimcoal2
* Download the version for your operating system e.g.
 `wget http://cmpg.unibe.ch/software/fastsimcoal26/downloads/fsc26_linux64.zip`

* Unzip and then make executable with `chmod +x fsc26`
  
* See our conda_instructions.md (https://github.com/SmithsonianWorkshops/Species_Delimitation_2021_08/blob/main/conda_instructions.md) and create an environment just for delimitR.
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
```
* Then download the delimitR code:
`git clone https://github.com/meganlsmith/delimitR.git`
* Unpack the tar.gz file
* Set your working directory to the directory above the delimitR directory that was created when you unpacked the source code.
* Try typing `which R` to make sure it's the version you just installed with conda.
* Start R by typing `R`
* And then install delimitR from within R:
```
devtools::install('delimitR', dependencies = TRUE)
```
