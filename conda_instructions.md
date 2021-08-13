# Conda
* Free & open source package management system
* Large community in data science and biology
* Started in Python community (hence snake reference) for data science
* No admin privileges required to install software if installed as suggested in this document
* Main development by a commercial company, Anaconda, that offers paid versions, but free version works great.

# Version of Anaconda/Miniconda
* Anaconda: distribution of conda with many data science tools pre-bundled
* Miniconda: minimal distribution of conda, other packages can be added: (star) What we suggest using

# Installing
* Download: We want the Linux, 64-bit, Python3 installer found on this page: https://docs.conda.io/en/latest/miniconda.html (Note: We recommend getting the Python3 installer even if you need Python2 for some programs. You can setup a separate Python2 environment)
* `$ wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh`
* If you don't have wget on your computer, you can download by clicking on the link to the version for your operating system instead.
* Run installer. Make sure to enter "yes" to "running conda init":

```
$ sh Miniconda3-latest-Linux-x86_64.sh
...
Do you accept the license terms? [yes|no]
[no] >>> yes
...
[/home/user/miniconda3] >>> [press enter key]
PREFIX=/home/user/miniconda3
...
Do you wish the installer to initialize Miniconda3
by running conda init? [yes|no]
[no] >>>yes
```
* Exit your shell and open a new one
* Look for (base) at the beginning of your command prompt. 
* Test with: which conda
```
(base) $ which conda
~/miniconda3/bin/conda
```
* (warning) If you don't see (base), and your shell is bash, there may be an issue with a config file in your home directory. You can fix this with: `nano ~/.bash_profile` and then append this text to the bottom of the file:
```
# Get the aliases and functions
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi
```
* Close your terminal and open a new one to see if (base) is now at the beginning of your command prompt.

### What did the installer do?
* `~/miniconda3/`: where all the conda programs are installed.
* `~/.bashrc `(for bash users, this file is run when you start a new bash shell): a command has been appended to enable conda (modifying your $PATH) and changing your prompt.
* `~/.conda/ and ~/.condarc`: hidden directory and file with settings

## Packages
* A conda package is the precompiled program and a link to all of the required packages that will also be downloaded and needed.
* A whole pipeline can be defined in a package: all the scripts and dependent software (e.g. qiime2 or phyluce)
* Packages are created by people in the community and shared publicly. Sometimes they’re created by the software developer, but they’re often by users of the software.
* You can create your own packages which a great method for reproducible science and collaboration. 

### Help with conda
`conda help`
`conda install --help`
* Online documentation: https://docs.conda.io/projects/conda/en/latest/commands.html

### Listing installed packages
* Some packages come pre-installed with miniconda (there would be a lot more if you were using the Anaconda installer)

`(base)$ conda list`
```
# packages in environment at /home/user/miniconda3:
#
# Name                    Version                   Build  Channel
_libgcc_mutex             0.1                        main
asn1crypto                1.2.0                    py37_0
ca-certificates           2019.10.16                    0
certifi                   2019.9.11                py37_0
cffi                      1.13.0           py37h2e261b9_0
chardet                   3.0.4                 py37_1003
conda                     4.7.12                   py37_0
conda-package-handling    1.6.0            py37h7b6447c_0
cryptography              2.8              py37h1ba5d50_0
...
```
### How to find conda packages
* You can search the public package repositories at https://anaconda.org/ (star) What we suggest using
* Use the anaconda.org search feature.
* Copy the install command from the package's page
* Or do a web search: "conda r" or "bioconda mafft"
* Or use conda search "blast" (finds packages with blast anywhere in their name in your current channels)

### Installing a package
`conda install ... `installs a packages and its dependencies
It doesn’t matter what your current directory is, it will install in your miniconda directory!
`(base)$ conda install -c bioconda mafft`
 
```
The following packages will be downloaded:
...
The following NEW packages will be INSTALLED:
...
Proceed ([y]/n)? y
Preparing transaction: done
Verifying transaction: done
Executing transaction: done
```
Test it:
```
(base)$ mafft --help
------------------------------------------------------------------------------
  MAFFT v7.471 (2020/Jul/3)
  https://mafft.cbrc.jp/alignment/software/
  MBE 30:772-780 (2013), NAR 30:3059-3066 (2002)
------------------------------------------------------------------------------
```
### Add bioconda and conda-forge to your channels
```
(base)$ conda config --add channels defaults
(base)$ conda config --add channels bioconda
(base)$ conda config --add channels conda-forge
```
`conda config --get channels` shows your current channels
* Which channel is the highest and which is the lowest?
`$ conda config --get channels`
`--add channels 'defaults'   `# lowest priority
`--add channels 'bioconda'`
`--add channels 'conda-forge'`   # highest priority
* conda-forge is the highest, defaults is the lowest.
* Note: the more channels you have, the increased time to "solve" installation.

`(base)$ conda install iqtree`
 
```
...
The following packages will be downloaded:
 
    package                    |            build
    ---------------------------|-----------------
    ca-certificates-2020.6.20  |       hecda079_0         145 KB  conda-forge
    certifi-2020.6.20          |   py37hc8dfbb8_0         151 KB  conda-forge
    conda-4.8.3                |   py37hc8dfbb8_1         3.0 MB  conda-forge
    iqtree-2.0.3               |       h176a8bc_0         2.8 MB  bioconda
    openssl-1.1.1g             |       h516909a_0         2.1 MB  conda-forge
    python_abi-3.7             |          1_cp37m           4 KB  conda-forge
    ------------------------------------------------------------
                                           Total:         8.2 MB
...
```
### conda install tricks

* Installing multiple items
`conda install mafft gblocks`
* “It is best to install all packages at once, so that all of the dependencies are installed at the same time.” https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-pkgs.html

### Specifying program versions
* Show available versions with: 
`conda search python`
`conda install python=3`
* =3 matches the most recent version starting with 3
* ==3.7.5 matches exactly the version specified
* ">3.7" matches most recent version greather than 3.7 (in quotes because of the > which will interfere with the shell's redirection features)
* "<3.8" matches most recent version less than 3.8 (in quotes because of the < which will interfere with the shell's redirection features)
* See the conda documentation for more information

### Wait, there's one more concept to keep things clean... environments
* So far all installs we've done have done into one set of packages called (base). What if programs have conflicting dependencies or you need different versions of the same program?
* A conda Environment is a compartmentalized set of packages:
* Also, the more packages you have, the longer it will take for conda on the "Solving Environment" step.

* What if you wanted to have both iqtree1 and iqtree2 installed? Above we showed how to installed iqtree.
* It installed the latest version: 2.0.3. If you also need iqtree 1.x installed, the conda command: `conda install iqtree=1 ` will downgrade your current iqtree from 2.x to 1.x, it won't allow you to have more than one version installed. You can have environments to have access to the two versions. (Using iqtree=1 will install the latest version of iqtree that starts with a 1).

### Creating an environment
`(base)$ conda create -n iqtree-v1`
*  To activate this environment, use
`$ conda activate iqtree-v1`

* To deactivate an active environment, use
`$ conda deactivate`

### Adding packages to the environment
`(base)$ conda activate iqtree-v1`
`(iqtree-v1)$ conda install iqtree=1`
* Note: you can create an environment and add packages do it in one step with: `conda create -n iqtree-v1 iqtree=1 `

### Removing an environment
* To remove an environment and all of its packages: (warning) You have to deactivate the environment before removing it
`(iqtree-v1)$ conda deactivate`
`(base)$ conda remove -n iqtree-v1 --all`
 
```
Remove all packages in environment /home/user/miniconda3/envs/iqtree-v1:
 
## Package Plan ##
 
  environment location: /home/user/miniconda3/envs/iqtree-v1
 
The following packages will be REMOVED:
...
Proceed ([y]/n)? y
```
### Useful environments: python2 and R
* If you need to a use a program written in python2, you can create an environment with that version of Python
`(base)$ conda create -n python2 python=2`
`(base)$ conda activate python2`
* You can use conda to install R and R packages
`(base)$ conda create -n tidyverse r r-tidyverse`
`(base)$ source activate tidyverse`
