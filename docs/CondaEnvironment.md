# Working Environment

For some of the exercises you'll need to have Python installed on your computer as well as some specific libraries. Of course you can install all that directly but if you want to be on the safe side, you can also setup a working environment first and install the packages there. Those packages will then only exist inside the environment and won't interfere with anything else you might have installed on your machine. [Conda](https://docs.conda.io/projects/conda/en/latest/index.html) is a very userfriendly option for that. It provides an environment and package management service for many programming languages (Python, C++, Java...) and can  run on Windows, Mac and Linux machines. For our purposes the light weight installer version called ''Miniconda'' will do.

You can install Miniconda very easily from it's [webpage](https://docs.conda.io/projects/miniconda/en/latest/). Download the installer and follow the instructions given for your machines respective operating system.

Conda can be started in the command line by just typing
```
conda activate
```

## Creating a Conda Environment

You can create a new conda environment by executing
```
conda create --name <name of your new environment> <list of package(s) to install>
```
You can give your environment whichever name you want. It will be stored in your conda install repository under 'envs'. 
You can always get a list of your environments by
```
conda info --envs
```
There are many possibilities for the packages to install. For this tutorial you will need to create an environment containing a Python version.
```
conda create --name <name of your new environment> python=3.9
```
If you are asked if you want to proceed, type 'y' for yes. Conda will now construct the environment for you. To work within it, you need to activate it first:
```
conda activate <name of your environment>
```
If you want to leave your environment, you can deactivate it:
```
conda deactivate
```

## Package Management

If you realize later on that you need additional packages in your environment, this is also no problem. Activate your environment and do
```
conda install <package name>
```
A list of available packages within conda is given [here](https://anaconda.org/anaconda/repo).
For the tutorial exercises, a good start would be to install the following packages:
```
conda install numpy pandas matplotlib jupyter notebook scipy seaborn
```
Be a bit patient when installing new packages, it might take a while. The advantage of installing many packages at once is that conda will automatically take care of any dependencies and versions.

If you'd like to deinstall a package, type
```
conda remove <package name>
```
inside the active environment. If you want to update a package to a newer version, do
```
conda update <package name>
```


## Updating Conda

You can check your conda version by just typing
```
conda --version
```
in the command line. If you want to update to a newer version of conda, you can do so by executing:
```
conda update -n base -c defaults conda
```
It might take a bit, don't worry.
