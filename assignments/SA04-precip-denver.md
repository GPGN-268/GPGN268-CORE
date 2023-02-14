# SA04 - Analyzing precipitation data.

### 🎯 Objectives: 
In this assignment, you will continue exploring meteorological data from the Denver Water Department. You will be evaluated by:
- Your choice of variable and file names throughout your code
- The style and level of documentation (comments ) in your code
- Your mastery over the concepts covered in the Python tutorials 4-7.
- Your interpretation of the data and figures

I encourage you to work with your peers on this assignment. 

### Preparation

Open your terminal and navigate to your  `ds00-python-intro` directory and launch Jupyter Lab (remember to run `activate conda` if on GitBash)

```
$ cd ~/work/classes/GPGN268/coursework-villasboas/ds00-python-intro
$ jupyter lab
```

In the notebooks directory, you should have the file  `ds00-meteo-denver.ipynb` from your previous assignment. You will continue working on the same notebook

After the last cell that you have for the maximum temperature analysis, create a new Markdown cell and add a sub-heading "Part II: Precipitation data". For each task below, create a Markdown Cell with the title of the task before start working on your code

### Task 1 - Visualizing the raw data
Load the data from the file `meteo_denver_precip_2000_2022.txt` and assign that to a variable. This data corresponds to the cumulative precipitation for each month during the years 2000-2022  in Denver, CO. 
- [ ] **Make a heatmap of the data with a colorbar**. You may change the colors of your plot by adding the argument `cmap="name_of_the_colormap"` to your plotting function. Learn more about colormaps [here](https://matplotlib.org/stable/tutorials/colors/colormaps.html)
- [ ] What is wrong with the data?
- [ ] How many bad measurements this dataset has?
- [ ] Replace the bad measurements with NaNs
- [ ] Use pcolormesh to plot the cleaned data
	- [ ] Label the axes of your plot appropriately. Make sure to add a colorbar.
- [ ] What do you see in the data? Is there anything you can say about precipitation in Denver from this figure? Write your observations in a cell below your figure.

### Task 2 - Visualizing distributions
- [ ] Make a histogram of the data - label the axes accordingly 
	- Try changing the number of bins in your histogram (check the documentation of the plt.hist function to learn how to do this) 
- [ ] What do you note from the overall distribution? Is this consistent with what you expected for precipitation?  How is this similar/different from the maximum temperature distribution?
- [ ] Do some research on the web for common statistical distributions ([here](https://www.itl.nist.gov/div898/handbook/eda/section3/eda366.htm) is a good start). Which one of these models do you think could be used to describe your data?

### Task 3 - Monthly average
- [ ] Compute the average precipitations as a function of the month and save that in a variable
- [ ] Compute the standard deviation as a function of the month and save that in a variable
- [ ] Plot the average precipitation as a function of the month and use the standard deviation to plot an error bar (either as a shading or as an actual bar) 
		- Label your axes appropriately 
- [ ] What do you see? How does this plot compare with the monthly average maximum temperature?

### Task 4 - Yearly average
- [ ] Compute the average precipitation across all months as a function of the year and save that in a variable.
- [ ] Plot the yearly average precipitation
- [ ] On the same plot, plot a horizontal line with the overall mean precipitation (check the documentation for the function `axhline` from matplotlib.pyplot)
- [ ] Label your axes appropriately
- [ ] What do you see? How does it compare with the maximum temperature plot? 

### Task 5 - Identifying extremes
- [ ] Using numpy, find exactly which year had the highest average precipitation and the year that had the lowest average precipitation. 
- [ ] Repeat the plot from Task 4 adding a red circle corresponding to the maximum and a blue circle corresponding to the minimum
- [ ] Add a legend indicating "maximum" and "minimum"

### Task 6 - Save your work
- [ ] Save your work. 
- [ ] Shut down your Jupyter Lab server.
- [ ] Add and commit your notebook.
- [ ] Push it to GitHub
