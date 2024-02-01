# Introduction to Jupyter Lab
#### 🎯 Learning Objectives: 
-   Explain what a library is and what libraries are used for.
-   Import a Python library and use the functions it contains.
-   Read tabular data from a file into a program.
-   Select individual values and subsections from data.
-   Perform operations on arrays of data.



#### Create a directory for the intro to Python  module
```
$ cd ~/work/classes/GPGN268/coursework-villasboas
mkdir -p ds00-python-intro/data
mkdir -p ds00-python-intro/notebooks
```

#### Getting the data for today's class
```
$ cd ~/work/classes/GPGN268/GPGN268-CORE
$ git pull
```

```
$ ls -RF
```

```
$ cd assignments/intro-python/data
$ ls -F
```

```
$ cp meteo*.txt ~/work/classes/GPGN268/coursework-villasboas/ds00-python-intro/data
```

Now let's navigate to our newly created directory 
```
$ cd ~/work/classes/GPGN268/coursework-villasboas/ds00-python-intro
```
And launch Jupyter Lab. On mac, we run


```
$ jupyter lab
```
On GitBash, we need first to activate conda

```
$ conda activate
$ jupyter lab
```

#### Loading data into Python
First lets add a Markdown header so we know what this notebook is about.

```markdown
# GPGN268 - Introduction to Python
**Author:** Bia Villas Boas

This notebook uses meteorological data from the Denver water department to introduce basic Python concepts.
```

We would like to process the Denver meteorological data using Python. But what is actually in these files? Let's use the terminal (or text editor) to take a look at the files using an additional tab  in Jupyter Lab. It looks like these files have numbers that are organized in columns and rows and separated by some white spaces.

To begin processing the meteorological data, we need to load it into Python. We can do that using a library called [NumPy](https://numpy.org/), which stands for Numerical Python. In general, you should use this library when you want to manipulate lots of numbers, especially if you have matrices or arrays. To tell Python that we’d like to start using NumPy, we need to import it:

```python
import numpy as np
```

Importing a library is like getting a piece of lab equipment out of a storage locker and setting it up on the bench. Libraries provide additional functionality to the basic Python package, much like a new piece of equipment adds functionality to a lab space. Just like in the lab, importing too many libraries can sometimes complicate and slow down your programs - so we only import what we need for each program.

Once we’ve imported the library, we can ask the library to read our data file for us:

```python
np.loadtxt(fname='../data/meteo_denver_tmax_2000_2022.txt', delimiter='\t')
```

The expression `numpy.loadtxt(...)` is a [function call](https://swcarpentry.github.io/python-novice-inflammation/reference.html#function-call) that asks Python to run the [function](https://swcarpentry.github.io/python-novice-inflammation/reference.html#function) `loadtxt` which belongs to the `numpy` library. The dot notation in Python is used most of all as an object attribute/property specifier or for invoking its method. `object.property` will give you the object.property value, `object_name.method()` will invoke on object_name method.

As an example, Mines Stadium is the stadium that belongs to Mines. We could use the dot notation to write  `mines.stadium`, just as `loadtxt` is a function that belongs to the `numpy` library.

`numpy.loadtxt` has two [parameters](https://swcarpentry.github.io/python-novice-inflammation/reference.html#parameter): the name of the file we want to read and the [delimiter](https://swcarpentry.github.io/python-novice-inflammation/reference.html#delimiter) that separates values on a line. These both need to be character strings (or [strings](https://swcarpentry.github.io/python-novice-inflammation/reference.html#string) for short), so we put them in quotes.

Since we haven’t told it to do anything else with the function’s output, the [notebook](https://swcarpentry.github.io/python-novice-inflammation/reference.html#notebook) displays it. In this case, that output is the data we just loaded. By default, only a few rows and columns are shown (with `...` to omit elements when displaying big arrays). Note that, to save space when displaying NumPy arrays, Python does not show us trailing zeros, so `1.0` becomes `1.`.

Our call to `numpy.loadtxt` read our file but didn’t save the data in memory. To do that, we need to assign the array to a variable. In a similar manner to how we assign a single value to a variable, we can also assign an array of values to a variable using the same syntax. Let’s re-run `numpy.loadtxt` and save the returned data:

```python
tmax = np.loadtxt(fname='../data/meteo_denver_tmax_2000_2022.txt', delimiter='\t')
```

This statement doesn’t produce any output because we’ve assigned the output to the variable `data`. If we want to check that the data have been loaded, we can type the variable’s name:

```python
tmax
```

Now that the data are in memory, we can manipulate them. First, let’s ask what [type](https://swcarpentry.github.io/python-novice-inflammation/reference.html#type) of thing `data` refers to:

```python
type(tmax)

```

```
<class 'numpy.ndarray'>
```

The output tells us that data currently refers to an N-dimensional array, the functionality for which is provided by the NumPy library. These data correspond to arthritis patients’ inflammation. The rows are the individual patients, and the columns are their daily inflammation measurements.

##### Data Type
A Numpy array contains one or more elements of the same type. The type function will only tell you that a variable is a NumPy array but won’t tell you the type of thing inside the array. We can find out the type of the data contained in the NumPy array.

```python
tmax.dtype
```

```
float64
```

This tells us that the NumPy array’s elements are floating-point numbers.

With the following command, we can see the array’s shape:

```python
print(tmax.shape)
```

```
(23, 12)
```

The output tells us that the `tmax` array variable contains 23 rows and 12 columns. When we created the variable `tmax` to store our temperature data, we did not only create the array; we also created information about the array, called [members](https://swcarpentry.github.io/python-novice-inflammation/reference.html#member) or attributes. This extra information describes `tmax` in the same way an adjective describes a noun. `tmax.shape` is an attribute of `tmax` which describes the dimensions of `tmax`. We use the same dotted notation for the attributes of variables that we use for the functions in libraries because they have the same part-and-whole relationship.

If we want to get a single number from the array, we must provide an [index](https://swcarpentry.github.io/python-novice-inflammation/reference.html#index) in square brackets after the variable name, just as we do in math when referring to an element of a matrix. Our inflammation data has two dimensions, so we will need to use two indices to refer to one specific value:

```python
print('first value in tmax:', tmax[0, 0])
```

```python
first value in tmax: 50.9
```

```python
print('middle value in tmax:', tmax[11, 6])
```

```python
middle value in tmax: 92.7
```

The expression `tmax[11, 6]` accesses the element at row 11, column 6. While this expression may not surprise you, `tmax[0, 0]` might. Programming languages like Fortran, MATLAB and R start counting at 1 because that’s what human beings have done for thousands of years. Languages in the C family (including C++, Java, Perl, and Python) count from 0 because it represents an offset from the first value in the array (the second value is offset by one index from the first value). This is closer to the way that computers represent arrays (if you are interested in the historical reasons behind counting indices from zero, you can read [Mike Hoye’s blog post](http://exple.tive.org/blarg/2013/10/22/citation-needed/)). As a result, if we have an M×N array in Python, its indices go from 0 to M-1 on the first axis and 0 to N-1 on the second. It takes a bit of getting used to, but one way to remember the rule is that the index is how many steps we have to take from the start to get the item we want.


#### Slicing data

An index like `[11, 6]` selects a single element of an array, but we can select whole sections as well. For example, we can select the first ten days (columns) of values for the first four patients (rows) like this:

```python
tmax[0:4, 0:6]
```

```
array([[50.9, 56.4, 57.5, 69.3, 78.2, 86. ],
       [48.2, 45.4, 54.8, 65.8, 73.8, 87.3],
       [47.7, 51.8, 51.7, 69.7, 73.1, 90.4],
       [54.7, 44.7, 54.6, 67.9, 73.8, 80.1]])
```

The [slice](https://swcarpentry.github.io/python-novice-inflammation/reference.html#slice) `0:4` means, “Start at index 0 and go up to, but not including, index 4”. Again, the up-to-but-not-including takes a bit of getting used to, but the rule is that the difference between the upper and lower bounds is the number of values in the slice.

We don’t have to start slices at 0:

```python
tmax[5:10, 0:6]
```

```
array([[49.2, 51.2, 55.4, 62.5, 73.8, 84.3],
       [54.5, 47.8, 53.5, 68.9, 74.9, 87.1],
       [30.6, 40.8, 58.5, 61.7, 72.5, 86.5],
       [40.1, 48.6, 54.8, 63. , 72.5, 85. ],
       [52. , 56.5, 60.5, 61.2, 73.7, 80.6]])
```

We also don’t have to include the upper and lower bound on the slice. If we don’t include the lower bound, Python uses 0 by default; if we don’t include the upper, the slice runs to the end of the axis, and if we don’t include either (i.e., if we use ‘:’ on its own), the slice includes everything:

```python
subset = python[:3, 6:]
print('subset is:')
print(subset)
```

The above example selects rows 0 through 2 and columns 36 through to the end of the array.

```
subset is:
[[94.7 93.  81.9 67.5 46.2 46.1]
 [95.3 90.6 86.  69.7 61.7 50.2]
 [96.  90.3 82.  63.3 52.3 50.6]]
```

#### Analyzing data

NumPy has several useful functions that take an array as input to perform operations on its values. If we want to find the average inflammation for all patients on all days, for example, we can ask NumPy to compute `tmax`’s mean value:

```python
np.mean(tmax)
```

```
67.9909420289855
```

`mean` is a [function](https://swcarpentry.github.io/python-novice-inflammation/reference.html#function) that takes an array as an [argument](https://swcarpentry.github.io/python-novice-inflammation/reference.html#argument).

Let’s use three other NumPy functions to get some descriptive values about the dataset. We’ll also use multiple assignment, a convenient Python feature that will enable us to do this all in one line.

```python
maxval, minval, stdval = np.max(tmax), np.min(tmax), np.std(tmax)

print('maximum max temperature:', maxval)
print('minimum max temperature:', minval)
print('standard deviation:', stdval)
```

Here we’ve assigned the return value from `np.max(tmax)` to the variable `maxval`, the value from `numpy.min(tmax)` to `minval`, and so on.

```python
maximum max temperature: 96.7
minimum max temperature: 30.6
standard deviation: 16.614984435991314
```


> #### Mystery Functions in IPython[](https://swcarpentry.github.io/python-novice-inflammation/02-numpy/index.html#mystery-functions-in-ipython)
> 
> How did we know what functions NumPy has and how to use them? If you are working in IPython or in a Jupyter Notebook, there is an easy way to find out. If you type the name of something followed by a dot, then you can use [tab completion](https://swcarpentry.github.io/python-novice-inflammation/reference.html#tab-completion) (e.g. type `numpy.` and then press Tab) to see a list of all functions and attributes that you can use. After selecting one, you can also add a question mark (e.g. `numpy.cumprod?`), and IPython will return an explanation of the method! This is the same as doing `help(numpy.cumprod)`. Similarly, if you are using the “plain vanilla” Python interpreter, you can type `numpy.` and press the Tab key twice for a listing of what is available. You can then use the `help()` function to see an explanation of the function you’re interested in, for example: `help(numpy.cumprod)`.

When analyzing data, though, we often want to look at variations in statistical values, such as the maximum max temperature per year or the average max temperature per month. One way to do this is to create a new temporary array of the data we want, then ask it to do the calculation:

```python
tmax_2000 = tmax[0, :] # 0 on the first axis (rows), everything on the second (columns)
print('maximum temperature in 2000:', np.max(tmax_2000))
```

```
maximum temperature in 2000: 94.7
```

Everything in a line of code following the ‘#’ symbol is a [comment](https://swcarpentry.github.io/python-novice-inflammation/reference.html#comment) that is ignored by Python. Comments allow programmers to leave explanatory notes for other programmers or their future selves.

We don’t actually need to store the row in a variable of its own. Instead, we can combine the selection and the function call:

```
print('maximum temperature in 2002:', np.max(tmax[2, :]))
```

```
maximum temperature in 2002: 96.0
```

What if we need the maximum temperature for each year over all months (as in the next diagram on the left) or the average across all years for each month (as in the diagram on the right)? As the diagram below shows, we want to perform the operation across an axis:

![[array-operations.png]]

To support this functionality, most array functions allow us to specify the axis we want to work on. If we ask for the average across axis 0 (rows in our 2D example), we get:

```python
np.mean(tmax, axis=0)
```

```
array([48.46521739, 47.93913043, 57.72173913, 65.00869565, 72.70434783,
       86.58695652, 92.50869565, 90.35652174, 82.69130435, 67.76956522,
       56.75652174, 47.3826087 ])
```

As a quick check, we can ask this array what its shape is:

```python
np.mean(tmax, axis=0).shape
```

```
(12,)
```

The expression `(12,)` tells us we have an N×1 vector, so this is the average max temperature per month for all years. If we average across axis 1 (columns in our 2D example), we get:

```python
np.tmax(tmax, axis=1)
```

```
array([68.975     , 69.06666667, 68.24166667, 68.34166667, 67.05833333,
       68.20833333, 65.125     , 64.35      , 66.65833333, 66.49166667,
       68.2       , 67.49166667, 71.26666667, 66.96666667, 67.80833333,
       68.59166667, 69.93333333, 69.03333333, 68.74166667, 66.875     ,
       69.14166667, 69.09166667, 68.13333333])

```

which is the average max temperature per year across all months.


#### Clear notebook and commit changes

In the Jupyter Lab toolbar click on `Kernel` then `Restart Kernel and Clear All Outputs`

Now, in the terminal, add you notebook to git, commit, and push to GitHub.

#### Exiting Jupyter Lab

Remeber to "shut down" your notebook by going to `File` in the top left corner and then `Shut Down`
