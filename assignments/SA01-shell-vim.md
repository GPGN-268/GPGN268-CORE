# 🪚 Sharpening the saw: Shell
The goal of this assignment is to practice some basic shell commands. Please read the full instructions before starting the assignment.  

#### PART I

Open a terminal and navigate to your main GPGN268 coursework folder, which should look something like this:

```
$ cd ~/work/classes/GPGN268/coursework-yourlastname/
```

Now, we will create a text file for this assignment using Vim.

```
$ vim shell-assigment.md
```

You will need to open a second terminal window to complete the rest of the assignment. Click anywhere on your current terminal (the one that has Vim opened) to make sure that window is active, and then press:
- **Mac**  → command + N
- **Windows** → alt + F2

This should open a second terminal window. At this point, you should have two windows side-by-side: one window with Vim opened and another terminal window with your usual command prompt. 

In the next part of this assignment, there will be several tasks. For each task you will need to run shell commands. After running each command on the terminal, you will type them in your text file. Like so


![shell-assignment-example](https://user-images.githubusercontent.com/2079352/213600579-25e458d8-24a4-4536-93bf-bb94b9e68044.png)


#### PART II

##### Task 1
 First, create a directory called `short-assignments` in your main GPGN268 coursework folder and then navigate to that directory. When you do that, `pwd` should look something like this:

```
 $ pwd
~/work/classes/GPGN268/coursework-yourlastname/short-assignments
```

##### Task 2
Download the folder `north-pacific-gyre` from Canvas, move it to `~/work/classes/GPGN268/coursework-yourlastname/short-assignments/`

and list the contents of  `north-pacific-gyre`.

##### Task 3
You will note that there are some `.txt` files that end with "A" and some that end with "B". Create two directories `NENE-A` and `NENE-B` and move the "A" files and "B" files to the respective directories.

##### Task 4 
Count how many lines there are in each of the "A" files and each of the "B" files and display that in a sorted way (with the number of lines decreasing from the top to the bottom). 

- Which file has the least number of lines?

##### Task 5
Delete the `.txt` files in the main `north-pacific-gyre` folder that end with "Z".

##### Task 6
- Save your `shell-assigment.md`
- Exit Vim
- Move your  `shell-assigment.md` to the `short-assignments` directory.
- Upload  `shell-assigment.md` to Canvas.
