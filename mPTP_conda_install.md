### Installing mPTP
* GitHub page: https://github.com/Pas-Kapli/mptp
* See our conda_instructions.md (https://github.com/SmithsonianWorkshops/Species_Delimitation_2021_08/blob/main/conda_instructions.md) and create an environment just for mPTP.
* This will avoid any dependency conflicts and allow you to install without root privileges.
* Next, install the necessary dependencies via conda:
```
conda install -c conda-forge bison
conda install -c conda-forge flex
conda install -c conda-forge autoconf
conda install -c anaconda automake
conda install -c salilab gsl
```
* Then download the mPTP code:
```
git clone https://github.com/Pas-Kapli/mptp.git
```
* Make sure you have a recent gcc version installed. This can also be done via conda (e.g. `conda install -c conda-forge gcc`).
* `cd` into the mPTP code directory
* run `./configure --prefix=/YOUR/PREFERRED/INSTALL/LOCATION`
* run `make`
* run `make install`
