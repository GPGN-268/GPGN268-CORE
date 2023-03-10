# Plotting

### Numpy array 101

```python
import numpy as np
np.arange(start, end, step) # gives you an array of range(start, end, step)
# for example, np.arange(1,10,2) will give you an array of [1,3,5,7,9]
# np.arange(5) will give [0,1,2,3,4]
# can give you floats too by setting the step to a float

np.linspace(start, end, n) # gives you an array of n number of values between start,end

# for getting max and min values in an array
np.amax() 
np.amin()

# some stats stuff
np.mean()
np.median()
np.std()
```

### For cute colors

[List of named colors - Matplotlib 3.6.0 documentation](https://matplotlib.org/stable/gallery/color/named_colors.html)

### General plotting

```python
import matplotlib.pyplot as plt

plt.figure(figsize=(5,5)) # or (10,5) for a long one
plt.title("title")

plt.plot(x, y, '') # put whatever decoration stuff in ''
# you can put in hex color codes to make it prettier
# ',' gives you a little pixel point, 'o' gives you a scatter plot

plt.xlabel("x")
plt.ylabel("y")

plt.xlim(xmin,xmax)
plt.ylim(ymin,ymax)
plt.grid(True) # show a grid

plt.show()
```

### Interactive plots

This magic command enables the backend in the Jupyter notebook

```python
%matplotlib notebook

# for ipyml backend, use
%matplotlib widget
```

### Making subplots

```python
import matplotlib.pyplot as plt

plt.figure(figsize=(10,5)) # for [fig1] | [fig2]

# plt.subplot(n. rows, n. columns, figure number)
# use fig, ax = plt.subplots() for advanced stuff (shown in more subplots)
plt.subplot(121)
plt.plot(x1, y1, '')
# add labels and limits

plt.subplots(122)
plt.plot(x2, y2, '')

plt.tight_layout() # for everything to show up correctly
plt.show()
```

### More subplots

[matplotlib.pyplot.subplots - Matplotlib 3.6.0 documentation](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.subplots.html)

### Invert axes

```python
plt.gca().invert_xaxis()
plt.gca().invert_yaxis()
```

### Find local max/min

```python
from scipy.signal import find_peaks

plt.plot(x[find_peaks(y)[0]], z[find_peaks(y)[0]], 'o')
```

### Interpolation

```python
np.interp(array_to_interpolate, x, y) # given x, y are known and array to interpolate has the size of the array size you want
```

### Find intersections

```python
np.argwhere(np.diff(np.sign(f - g))).flatten() # given arrays f, g
# remember to interpolate the arrays enough for accurate results
```

### Legend box outside the plot

```python
plt.legend(bbox_to_anchor=(0.6, -0.1), loc="upper left") # change loc for anchor
```

### Add lines

```python
plt.hlines(y = subset.daxis[change_i],
           xmin=np.min(avg_temp)-5, xmax=np.max(avg_temp)+5,
           colors='r', linestyles='dashed',
           label='section change')
```

### Text in plot (annotation)

```python
plt.annotate('Vertical',xy=(150,0), xytext=(50, 7500), xycoords = 'data')
```

### Example plot

```python
plt.figure(figsize=(2,6))
plt.plot(avg_temp, subset.daxis)
plt.hlines(y = subset.daxis[change_i],
           xmin=np.min(avg_temp)-5, xmax=np.max(avg_temp)+5,
           colors='r', linestyles='dashed',
           label='section change')
plt.annotate('Vertical',xy=(150,0), xytext=(50, 7500), xycoords = 'data')
plt.annotate('Horizontal',xy=(150,0), xytext=(50, 8500), xycoords = 'data')
plt.title("Averaged temperature vs fiber distance")
plt.xlabel("temperature (°F)"); plt.ylabel("Depth (ft)")
plt.gca().invert_yaxis()
plt.legend(bbox_to_anchor=(0.5, -0.1), loc="upper center")
plt.show()
```

### Making it fancy with LaTeX (Thanks Paul!)

```python
import matplotlib.pyplot as plt
plt.rc('text', usetex=True)
font = {'color':'black','size':16}
plt.rcParams.update({'font.size': 16})
```