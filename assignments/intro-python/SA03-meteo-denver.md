# SA03 - Python Basics

### 🎯 Objectives: 
In this assignment, you will begin exploring meteorological data from the Denver Water Department. You will be evaluated by:
- Your choice of variable and file names throughout your code
- The style and level of documentation (comments ) in your code
- Your mastery over the concepts covered in the Python tutorials 1-3.
- Your interpretation of the data and figures

I encourage you to work with your peers on this assignment. 

#### Preparation

Open your terminal and navigate to your  `ds00-python-intro` directory and launch Jupyter Lab (remember to run `activate conda` if on GitBash)

```
$ cd ~/work/classes/GPGN268/coursework-villasboas/ds00-python-intro
$ jupyter lab
```

In Jupyter Lab, using the directory tree on the left,  navigate to the directory `notebooks` and open a new notebook. Rename your notebook to `ds00-meteo-denver.ipynb`. Edit your notebook such that the header looks like this:

![[jupyter-header.png]]

For each task below, create a Markdown Cell with the title of the task before start working on your code

#### Task 1 - Visualizing the raw data
Load the data from the file `meteo_denver_tmax_2000_2022.txt` and assign that to a variable. This data corresponds to the maximum temperature recorded for each month during the years 2000-2022  in Denver, CO. 
- [ ] **Make a heatmap of the data with a colorbar**. You may change the colors of your plot by adding the argument `cmap="name_of_the_colormap"` to your plotting function. Learn more about colormaps [here](https://matplotlib.org/stable/tutorials/colors/colormaps.html)
- [ ] Label the axes of your plot appropriately
- [ ] What do you see in the data? Is there anything you can say about the maximum temperature from looking at this plot? Write your observations in a cell below your figure.


### Task 2 - Visualizing distributions

- [ ] Make a histogram of the data - label the axes accordingly 
	- Try changing the number of bins in your histogram (check the documentation of the plt.hist function to learn how to do this) 
- [ ] What do you note from the overall distribution? What happens when you change the number of bins? Write your observations in a cell below your plot

### Task 3 - Monthly average

- [ ] Compute the average maximum temperature as a function of the month and save that in a variable
- [ ] Compute the standard deviation as a function of the month and save that in a variable
- [ ] Plot the average maximum temperature as a function of the month 
		- In the same figure, plot the average - standard deviation and average + standard deviation. Your figure will have three lines. 
		- Label your axes appropriately 
- [ ] What do you see? How does this plot relate to the plot in Task 1?  On average, what month has the highest maximum temperature? What month has the highest standard deviation?

### Task 4 - Yearly average
- [ ] Compute the average maximum temperature across all months as a function of the year and save that in a variable.
- [ ] Plot the yearly average maximum temperature.
- [ ] What do you see? How does that compare with the plot you made in Task 1?  What year was the warmest on average? What year was the lowest maximum temperature on average?

### Task 5 - Save your work
- [ ] Save your work. 
- [ ] Shut down your Jupyter Lab server.
- [ ] Add and commit your notebook.
- [ ] Push it to GitHub
