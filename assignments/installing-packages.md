
## Installing packages in the GPGN268 environment

We have briefly talked about python environments and package managers. I explained that there was a package manager called `mamba` that installs python packages much faster than `conda`. However, we didn't manage to get `mamba` working on Windows, so we will keep using `conda`.

We created a python environment named `GPGN268`, so let't go ahead and activate that environment. Open a terminal or Gitbash and run:

```
$ conda activate GPGN268
```

You should now see the name of your environment in parentheses in your terminal. Something like this:

```
(GPGN268) $
```

Now, we will install a couple of packages in your environment using conda. We will need these packages in the next couple of lectures. Make sure you do this when you have a reliable internet connection for at least 30 min (it might take longer to install some packages).  Run the commands below and when prompted to answer yes/no to proceed, type "y".  

##### Installing [matplotlib](https://matplotlib.org/stable/index.html)
```
$ conda install -c conda-forge matplotlib
```

#### Installing [ipympl](https://matplotlib.org/ipympl/)
```
$ conda install -c conda-forge ipympl
```

##### Installing [cartopy](https://scitools.org.uk/cartopy/docs/latest/)
```
$ conda install -c conda-forge cartopy
```

##### Installing [pandas](https://pandas.pydata.org/)
```
$ conda install -c conda-forge pandas
```

##### Installing [xarray](https://docs.xarray.dev/en/stable/)
```
$ conda install -c conda-forge xarray
```

##### Installing the `nc-time-axis` extension
```
$ conda install -c conda-forge nc-time-axis
```
