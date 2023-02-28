# Python packages and environments

## Python Packages

When working with a programming language, such as Python, that can do almost _anything_, one has to wonder how this is possible. If you download Python, it has about 25 MB, how can everything be included in this small data package? The answer is - it is not. Python, as well as many other programming languages, uses external libraries or packages for being able to do almost _anything_. 

When you installed the Anaconda distribution of Python, it already came with several packages that we have been using in this course, such as matplotlib. For the next couple of lectures, we will learn how to use a library called [pandas](https://pandas.pydata.org/), but if we try to import pandas we will get an error

```python
import pandas as pd
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ModuleNotFoundError: No module named 'pandas'
```

`pandas` was not installed with Anaconda, so we need to use a package manager to download and install `pandas` for us.

## Package manager
One option for is to manage packages with `conda` which we have available from out Anaconda installation. From the [official Conda documentation](https://conda.io/projects/conda/en/latest/index.html). Conda is an open-source package and environment management system that runs on Windows, Mac OS, and Linux.

-   Conda can quickly install, run, and update packages and their dependencies.
-   Conda can create, save, load, and switch between project-specific software environments on your local computer.
-   Although Conda was created for Python programs, Conda can package and distribute software for any language such as R, Ruby, Lua, Scala, Java, JavaScript, C, C++, FORTRAN.

Conda as a _package manager_ helps you find and install packages. Python coupled with a package and environment manager provides a way to make isolated, reproducible _environments_ where you have fine-tuned control over all packages and configurations. **You should always work within an environment**, rather than the “default” environment.

It is strongly recommended to read official [Getting Started with Conda](https://conda.io/docs/user-guide/getting-started.html) guide.

To create a conda environment, you execute the following command:

```
$ conda create --name GPGN268 python=3.10 numpy
```

This will create a special environment in `$MINICONDA_HOME/envs/my_environment` with only Python and numpy to begin with. Here, we’ve also told conda to install Python version 3.10; you can specify exact versions or minima, and conda will take care of figuring out all the compatibilities between versions for you. To use this environment, simply “activate” it by executing:

```
$ conda activate GPGN268
```

Regardless of your shell, you should now see the string `(my_environment)` prepended to your prompt. Now, if you execute any Python-related tool from the command line, it will first search in `$MINICONDA_HOME/envs/my_environment/bin` to find them.

You can deactivate your environment by typing:

```
$ conda deactivate
```

To see all the environments on your system:

```
$ conda info --envs
```

If you want to permanently remove an environment and delete all the data associated with it:

```
$ conda remove --name my_environment --all
```

For extensive documentation on using environments, please see [the conda documentation](https://conda.io/docs/using/envs.html). The most important feature to review here is the ability to _share and export_ your environment; this is the basis for reproducibility in the scientific Python stack. At any time from the shell, you can execute


## Installing More Packages
Once you have a basic Python environment, you can easily add or remove packages using conda. Conda was created to help manage the complex dependencies and pre-compiled binary libraries that are necessary for scientific python.

To install packages, first, you activate the environment that you would like to work on:

```
$ conda activate GPGN268
```

Then, you can install packages from an official, curated set of packages which are built and tested for a number of different system configurations on Linux, Windows, and macOS

```
$ conda install matplotlib
```

Additionally, there is a community-maintained collection of packages/recipes called [conda forge](https://conda-forge.github.io/%3E) which is accessible through conda as a special “channel”

```
$ conda install -c conda-forge jupyterlab
```

While conda allows you to install almost any science-related package, there may be other general-use python packages you wish to you that are not available in via conda. For these, you can use an alternative installation method.

Outside of the scientific python community, the most common way to install packages is to search for them on the official [PyPI](https://pypi.python.org/pypi) index. Once you’ve found the package you want to install (you may have also just found it on github or elsewhere), you use the **pip** command from a the command line:

```
$ pip install <package-name>
```

### Note on channels and Conda Forge

Where do conda packages come from? The packages are hosted on conda [“channels”](https://conda.io/projects/conda/en/latest/user-guide/concepts/channels.html). From the conda docs:

> Conda channels are the locations where packages are stored. They serve as the base for hosting and managing packages. Conda packages are downloaded from remote channels, which are URLs to directories containing conda packages. The conda command searches a set of channels. By default, packages are automatically downloaded and updated from the default channel [https://repo.anaconda.com/pkgs/](https://repo.anaconda.com/pkgs/) which may require a paid license, as described in the repository [terms of service](https://www.anaconda.com/terms-of-service) a commercial license. The conda-forge channel is free for all to use. You can modify what remote channels are automatically searched. You might want to do this to maintain a private or internal channel. For details, see how to modify your channel lists.
> 
> Conda-forge is a community channel made up of thousands of contributors. Conda-forge itself is analogous to PyPI but with a unified, automated build infrastructure and more peer review of recipes.

Don’t be worried by the “commercial license part”. The Anaconda channel terms of service clearly excludes all educational activities and all research activities at non-profit institutions from their definition of commercial usage. Even companies with fewer than 200 employees are excluded. The aim of the commercial paid license for Anaconda is to require large corporations which use the repository heavily to contribute financially to its maintenance and development. Without such contributions, Anaconda might not be able to sustain itself.

Despite this, I still recommend **always using the conda-forge channel for your python environments**. The reason are as follows:

-   Conda Forge is always free from commercial license restrictions
-   Conda Forge generally has the largest volume of packages and the most up-to-date versions
-   You can contribute your own packages to conda forge! This is not covered by this book, but you can read about it in the [Conda Forge docs](https://conda-forge.org/docs/maintainer/adding_pkgs.html).

## Speeding things up with Mamba

In order to put together an actual python environment from your package specifications, conda has to solve a difficult puzzle. Each package specified has certain dependencies on other packages. For example, Xarray depends on Numpy, Pandas, and several others. Moreover, each version of Xarray requires certain minimum versions of other packages (e.g. Xarray 0.19 requires Numpy >= 1.17 and Pandas >= 1.0). Other packages in your environment may have different or incompatible versions. Finding a combination of packages that are mutually compatible can be framed mathematically as a [boolean satisfiability problem](https://en.wikipedia.org/wiki/Boolean_satisfiability_problem).

The default “solver” of this problem for conda can be [slow](https://www.anaconda.com/blog/understanding-and-improving-condas-performance) It is not unheard of to spend 30 minutes or more solving large environments! 😱 

Fortunately, a much faster alternative called [mamba](https://github.com/mamba-org/mamba) has recently come out. To install it, just run:

```
$ conda install -c conda-forge mamba
```

Now you can install environments and packages as before, but using the `mamba` command instead of `conda`. Everything will be faster.
