---
layout: article
title: Setting up Python on OzSTAR
author: Adam Batten
show_author_profile: true
sharing: true
aside:
  toc: true
cover: /assets/images/OzStar_logo.png
date: 2021-02-02
modify_date: 2021-02-02
tags: tutorial supercomputing python ozstar

---

## Getting Started with using Conda Environments on OzStar

This is a short guide on how to set up Python on [OzSTAR](https://supercomputing.swin.edu.au/ozstar/), the supercomputer located at the [Swinburne University of Technology](https://www.swinburne.edu.au/). This will guide you through setting up [Conda enviroments](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) and some of the pitfalls you may encounter along the way. Keep in mind this isn't necessarly the 'perfect' way to use python on OzSTAR (since it really depends on your use case), but this tutorial is a good recommendation to get started for most people.

If you are unfamiliar with [Conda environments](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) before this guide, they may feel a little different, but will make using Python on OzSTAR significantly easier in the long run. 

Note: This is primarily aimed at people that will be using OzSTAR, and may not be applicable in other circumstances. 
{:.warning}

### This Tutorial Covers:
- [Preparation](#preparation)
- [Loading Anaconda](#loading-anaconda)
- [Using Conda Environments](#using-conda-environments)
  - [Why Use a Conda Environment?](#why-use-a-conda-environment)
  - [Creating a Conda Environment](#creating-a-conda-environment)
  - [Activate a Conda Environment](#activate-a-conda-environment)
  - [Deactivate a Conda Environment](#deactivate-a-conda-environment)
- [Issues With Home Directory Quota](#issues-with-home-directory-quota)


### This Tutorial Assumes You Can:
- Log into OzSTAR
- Can edit a text file (specifically your `.bashrc` or `.bash_profile`)

### Some Key Definitions:
- [Anaconda](https://www.anaconda.com/): A distribution of python designed for scientific computing. By installing Python through Anaconda, it makes managing and installing Python packages/versions much easier. In particular, Anaconda has a useful feature called '`conda` environments' which allows us to use different versions of Python or Python packages when we need to.
- `conda`: A package and environment manger that is bundled with [Anaconda](https://www.anaconda.com/). It can install packages similar to how `pip` can install Python packages from [PyPI](https://pypi.org/) using `conda install`. It can also create environments using `conda create`.
- `.bashrc`: This is a Bash shell script that runs whenever you launch an interactive shell. You can put any command(s) in a `.bashrc` that you would write at the command prompt. Then every time you launch a new interactive shell all the commands in the `.bashrc` will be executed. It is common practice to customise your `.bashrc` to include your own preferences (e.g. [aliases](https://en.wikipedia.org/wiki/Alias_(command)) for specific commands that you type often). You can find your `.bashrc` in your home directory (`~/.bashrc`).
- `PATH`: `PATH` is an environment variable that specifies a colection of directories where programs are located. This is list of directories are locations where programs can be started without having to type the entire path (e.g. `/User/username/subfolder/otherfolder/program.exe`). For example: to run Python you would normally just use the prefix `python`, without specifying where Python is located. This is because `python` is already the system `PATH`. If there are multiple directories in `PATH` that the required program, the one that will be used is the one that was added to the `PATH` the latest.

## Preparation

To get started, make sure that there is absolutely nothing related to Python environments currently found anywhere in your home directory or module lists.
This includes loading any of the OzSTAR Python modules (including Anaconda), like Python; [NumPy](https://numpy.org/); [Matplotlib](https://matplotlib.org/); etc, or having any conda installation (like [Anaconda](https://www.anaconda.com/) and [Miniconda](https://docs.conda.io/en/latest/miniconda.html)). 
Loading modules or libraries that are required by Python packages is fine.

You can ensure that all modules have been unloaded from your session use `module perge`.

In case you are unfamiliar, OzSTAR uses modules to manage the software it has installed. If you want to use a module you first have to load it. To load a module use the following command: `module load <module_name>/<software_version>`.
You can search for modules using `module spider <module_name>`. To view a list of all the modules you have loaded use `module ls`.
{:.info}

## Loading Anaconda
For managing Python on OzSTAR I suggest using Anaconda3 and `conda` environments. 

Despite its name, Anaconda3 is can be used for both Python 3 and Python 2 ([see warning about using Python 2](#python-3-vs-python-2)).
However Anaconda3 has the tendancy to overwrite the `PATH` to certain libraries that are used for Python packages. Examples of this include the HDF5-library [h5py](https://h5py.org/) and the MPI-library [mpi4py](https://mpi4py.readthedocs.io/en/stable/). It is a good idea to use the system modules on OzSTAR (except for the system Python) as they are compiled and optimized for the OzStar architecture. Therefore if you have a list of system modules that need to be loaded, make sure to load `anaconda3` first so that the other modules will overide the `anaconda3` paths as they are loaded. Loading all modules after `anaconda3` means that those corresponding libraries are found earlier in the system `PATH` than `anaconda3`'s libraries. This ensures that everything is found in the correct place. To do this you can execute the following: 

```
module purge
module load anaconda3/5.0.1
<load other modules>
```
The reason for using `module purge` all loaded modules first is to make absolutely sure that no paths are being overridden by `anaconda3`. I highly recommend using your `.bashrc` or `.bash_profile` for this, such that you don't have to do it manually every time you login.

The reason for using `anaconda3/5.0.1` rather than `anaconda3/5.1.0` (which is also available on OzSTAR), is because the latter version has a bug where OzSTAR will not correctly set the paths to Anaconda's commands (like `conda`; `activate`; `deactivate`). Instead, it attempts to use the ones from `anaconda3/5.0.1` whenever any environment besides the default is [activated](#activating-an-anaconda-environment). This means that it once an environment is [activated](#activating-an-anaconda-environment) using `anaconda3/5.1.0`, it becomes impossible to [deactivate](#deactivate-an-anaconda-environment) the environment again.
{:.warning}


<b>Example:</b>

If everytime I want to log into OzSTAR I load the modules `anaconda3`, `openmpi`, `hdf5` and `git`, to avoid having to type these out every single time I put this code into my `.bashrc` file. Note that the `anaconda3/5.0.1` comes directly after `module purge`.
```
module purge
module load anaconda3/5.0.1
module load openmpi/3.0.0
module load hdf5/1.10.1
module load git/2.16.0
```

## Using Conda environments

TL;DR: Create custom environments using `conda create -n <env_name> python==<python_version>`, activate with `source activate <environment_name>` and deactivate with `source deactivate`.
{:.success}

### Why use a Conda Environment?
The main purpose to using `conda` environments is to create an isolated environment for your project. This means you don't have to worry about if different projects you are working on require different versions of software.

Say for example that you are writing some code for one of your projects. This project requires Python > 3.5. However, in a different project at the same time you are using someone else's software that is only compatible with `Python 2.7`, you really have five choices:

1. Uninstall and reinstall Python every single time you swap between the different software (__tedious and not fun__).
3. Re-write the other software to be Python 3 compatible (__also not fun__).
2. Re-write all your software to be compatible Python 2.7 compatible (__not fun and will be more limited in features and support__).
4. Give up entirely (__really really not fun__).
5. Use different `conda` environments to swap between Python 2.7 and Python 3 easily.


### Creating a Conda Environment

The first rule about using a `conda` environment is NEVER use the base/default `conda` environment (i.e. the one that is activate with `source activate` with no additional arguments).
This environment is available to everyone that uses the same `anaconda3` module, and therefore cannot be used in a personal manner.
It also does not allow for packages to be installed globally (within the environment), which certain Python packages cannot deal with.
This is generally a good idea to avoid as well on personal computers.

So for this reason you will have to first create an new custom environment. A new environment can be created as follows:
```
conda create -n <environment_name> python==<python_version>
```
This will create an environment with the name `<environment_name>` using Python version `<python_version>`. This environment will be stored in your `~/.conda/envs` directory. You can create multiple environments for the different versions of Python required. I personally have a `Python 3.8` environment for 99.9% of my work and `Python 2.7` environment to run software that hasn't been update to `Python 3` yet.

If you dont know what to name your environment, I would suggest naming your environment either after the Python version. i.e If you are going to be using `Python 3.8`, name the environment `py38`, or you are using `Python 2.7` name it `py27`.

### Activate a Conda Environment
After the environment has been made, it can be activated with `source activate <environment_name>` (or `. activate <environment_name>`, either one is fine). You will be able to see that your environment is activated because the `<environment_name>` will appear on the left hand side of your prompt as shown below.

```
[~] conda activate py38
(py38) [~]
```

After you activate your environment, packages can be installed using `pip` or `conda` as normal without having to use the `--user` flag (which installs a package locally, but as environments are isolated, that is not necessary).

It's also convenient to include the `source activate <environment_name>` in your `.bashrc` or `.bash_profile` so that your environment is automatically activated when you log into OzSTAR. For example, I have an environment called `py38` and my `.bashrc` contains this:

```
module purge
module load anaconda3/5.0.1
source activate py38

module load openmpi/3.0.0
module load hdf5/1.10.1
module load git/2.16.0
```

### Deactivate a Conda Environment
To deactivate an active environment use `source deactivate` ( or `. deactivate`).

Keep a note of the [issue with deactivating environments](#loading-anaconda) if you use `anaconda3/5.1.0`.


## Issues with Home Directory Quota
TL;DR: If you are running out of inode space in your home directory, you can move your `.conda` to Lustre with `mv /home/<username>/.conda /fred/oz<group_number>/<username>` and make a symbolic link with `ln -s /fred/oz<group_number>/<username>/.conda /home/<username>/.conda`
{:.success}

The main downside with using this approach to use Python on OzSTAR is that `conda` environments produce a large number of small files.
If you have many environments or large ones, it is possible that you will hit the file limit (aka inode limit) in your home directory (which is set to 100k).

A solution to this is to move the `.conda` folder to a project on Lustre (`/fred/`) and making a symbolic link between its location and your home directory.

```
mv /home/<username>/.conda /fred/oz<group_number>/<username>
ln -s /fred/oz<group_number>/<username>/.conda /home/<username>/.conda
```

This will allow you to use your environments anywhere as if they were still located in your home directory.
However keep in mind that Lustre is designed for long-term, big-file storage and therefore is not nearly as fast with reading as the home directories are.
This means that activating an environment or executing a script can take a while to start up (often about 30 seconds to 1 minute).
Once started, there are no speed differences as all required scripts and modules have now been loaded.
So in effect, the first Python script you run in your session will take about a minute longer to run, but the rest will be exactly the same.

## Python 3 vs. Python 2
It is advised that you should be using Python 3 for almost all of your projects. As of the 1st of January 2020, Python 2 is no longer supported. Meaning that packages like [NumPy](https://numpy.org/), [Matplotlib](https://matplotlib.org), [SciPy](https://scipy.org) and [Astropy](https://astropy.org) (plus more) will no longer update or fix issues with the Python 2 version of the software. If you absolutely need to use Python 2 for a specific project (e.g. legacy code that hasn't been ported into Python 3 yet), you can set up a Python 2.7 environment and a Python 3 environment. 
{:.warning}

## Acknowledgements
A big thank to [Ellert van der Velden (@1313e)](https://github.com/1313e/) who wrote the backbone of this tutorial in a text document one day on Slack and for useful feedback on my interpretation of the document that I have presented in this article.

