# Lecture 04 – Working With Files and Directories (part 2)
#### 🎯 Learning Objectives: 
-  Delete files and directories
-  Create and edit files using an editor
-  Check the content of a text file using cat, head, tail, and wc
- Use wildcards and pipes to operate on multiple files and combine operations


#### Moving and Renaming Files (cont.)

In our last lecture, we learned how to use the command ` mv` which stands for "move". The syntax is `$ mv source target`, where `source` and `target` can be given both in terms of the absolute path or the relative path. We used `mv` to move our well-log-data directory from the Desktop to our project folder

For example

![filesystem-project](https://user-images.githubusercontent.com/2079352/213586440-5dc6aaa0-95c9-47f2-93f0-8891f93b8ad8.png)


if `$ pwd` shows `$  ~/work/classes/GPGN268/ds01-well-log`, we can run

```
$ mv ~/Desktop/well-log-data data/
```

```
$ ls -F data
well-log-data/
```

If we check the content of `well-log-data`, we see that there is a file called `iodp-usio-acronyms.html`. If we Google "IODP" we will find the website of the [International Ocean Drilling Program](https://www.iodp.org/), so it seems like these data might have come from IODP. Let's try to explore IOPD's website to see if we can find any additional information. With a little bit of digging (pun intended), we arrive at a data repository hosted on a [website from Columbia University](https://mlp.ldeo.columbia.edu/logdb/scientific_ocean_drilling/). There we can search for data from different IODP expeditions and also different holes. By inspection, it seems like our files follow this naming convention (`expedition-hole-XXXX.csv`). Let's try to find one specific mission and hole number that matches a file that you have in your dataset.

Now, considering that the data that you downloaded from Canvas came from IODP, is there anything that we could do to make the name of the directory  `well-log-data` more expressive?

The command `mv` can be used to move but also to **rename** files and directories. let's try:
```
$ cd data
$ mv well-log-data iodp-logging-data
$ ls -F
```

We found the original source of our well-log data and also lots of information that could be useful for our analysis and for our future selves. Following the best practices that we discussed in the File and Directory Organization section, let's create a README file explaining what the data is and where it came from.

#### Creating files

**Which editor?**
For this part of the lecture, we will learn the basics of a text editor called [Vim](https://www.vim.org/). The first thing that you might ask is "Do I really need to learn this? It seems pretty outdated..." I have been using Vim since I started coding as an undergrad just like you. I could spend a whole lecture convincing you that should still use Vim even when there are many modern text editors available (such as [VS Code](https://code.visualstudio.com/), [Sublime](https://www.sublimetext.com/), and [Notepad++](https://notepad-plus-plus.org/)), but I won't. Instead, I will share a few reasons why **I** use Vim. 
- **Vim is always available.** I do most of my work on remote machines, which operate on Linux and where I have no [graphical user interface](https://en.wikipedia.org/wiki/Graphical_user_interface) (GUI) to interact with, and no permission to install programs. Knowing Vim means that I can write code and edit files in the same way, no matter where I'm working. 
- **Vim has been around for 3 decades and ain't going anywhere.** While modern text editors and [IDEs](https://en.wikipedia.org/wiki/Integrated_development_environment) have several cool features that can make writing coding and editing text very efficient, in technology, tools hardly stick around for long. I don't want to invest time and energy learning all the tricks of a particular text editor when the chances that it will eventually stop working are pretty high (as it's the case for [Atom](https://github.blog/2022-06-08-sunsetting-atom/)).
- **Vim saves me time**. Vim is light and fast. There is basically no latency for opening and editing files. It is also highly customizable without the need of installing anything extra. Most importantly, once I learned the basics of Vim and build some muscle-memory it's nearly impossible for me to be as efficient using something else.

In this course, you will need some basic Vim skills, so this is what we will focus on. No matter what career path you choose, using Vim to open a file, add and delete text, and save it is something that will be useful to know. Advanced Vim can be extremely powerful and I encourage you to check out this [Vim cheat sheet](http://www.viemu.com/a_vi_vim_graphical_cheat_sheet_tutorial.html), the [official Vim documentation](https://www.vim.org/docs.php) as well as this [interactive Vim tutor](https://www.openvim.com/) if you are interested in learning more.

##### Getting started with vim 
Now let's navigate to our data directory and create a text file using Vim.

```
$ cd iodp-logging-data
$ vim README.md
```

The syntax `$ vim filename` can be used to create or open an existing file, where `filename` represents the target file you want to create or modify. The most important thing about Vim is that it has multiple modes. Here are three that we will use in this course:

| Mode    | Description                                 |
| ------- | ------------------------------------------- |
| Normal  | Default; for navigation and simple editing  | 
| Insert  | For explicitly inserting and modifying text |
| Command | For operations like saving, exiting, etc.   |

If you try to type, nothing will happen because Vim is in its default mode (normal). To be able to type, we switch to " insert" mode by typing `i`, which stands for " insert". Let's go ahead and try to type some information about our data. 

``` Markdown
## General information
last modified: YYYY-MM-DD
date created: YYYY-MM-DD
author: Blaster
## Dataset Information
- General Description: files containing well-logging data from the International Ocean Drilling Program (IODP)
```

Now, to go back to normal mode we hit `esc`. Now, we would like to save our file. To do that, we enter ` :` to go to command mode. Note that a colon appeared at the bottom of the page. This indicates that Vim is ready for our command. In this case, we want to "write" (which is the same as save) and the command for that is `w`. To run the command we hit "return" To exit vim we run `q`, from "quit". 

Now, if you run
```
$ ls -F
```

you should see the file that we just created.


### 👀 Checking the content of a file

😸 ` cat`: If we want to take a quick look at the content of a plain text file, we can use the command `cat`. For example, for the file that we just created we can run

```
$ cat README.md
```

This will print the entire file content on the screen, so it's not ideal if you only want to check a portion of the file. Try for example to run `cat` on one of the `.csv ` IODP files.

Another approach to take a quick look at the contents of a file is to use the commands `head` and `tail`.

```
$ head 372-U1520B_den-nscope.csv
```

⏬   `head` will show the first couple of lines of a file starting from the top, while

```
$ tail 372-U1520B_den-nscope.csv
```

⏫  `tail ` will show the last couple of lines of a file starting from the bottom. 

You can also specify how many lines you would like to see using the flag `-n`

```
$ tail -n 10 372-U1520B_den-nscope.csv
```

```
$ head -n 2 README.md 
```

Another simple task that might be handy is to count how many lines there are in a file. 

```
$ wc README.md
4    11    90    README.md
```

∑ `wc` tells the total number of lines, words, and bytes in the input argument (in this case, the file `README.md`).

####  Wildcards

Oftentimes one needs to do something (e.g., move) to several files at once. This can be done by providing a list of individual filenames, or specifying a naming pattern using wildcards.

`*` is a wildcard, which matches zero or more characters. Let’s consider the `iodp-logging-data` directory: `*.csv` matches `372-U1517A_cali-nscope.csv`, `372-U1517A_gr-gvr.csv`, and every file that ends with `*.csv`. On the other hand, `376*.csv` only matches the files starting with `376`.

When the shell sees a wildcard, it expands the wildcard to create a list of matching filenames before running the command that was asked for. As an exception, if a wildcard expression does not match any file, Bash will pass the expression as an argument to the command as it is. For example, typing `$ ls *.txt` in the `iodp-logging-data` directory results in an error message that there is no file called `*.txt`. 

You can place multiple wildcards at any part of a name. For example, in our logging data, we have files from three different holes (U1517A, U1520A, U1520B) for expedition 372. If we want to list all files from hole U1520A, we can run

```
$ ls *U1520A*.csv
```

This will list all files that have filenames with any pattern before `U1520A`, any pattern after  `U1520A`, and that end with `.csv`.

Wildcards can be used with other commands too (not only `ls`). For example, if we want see how many lines are in all files from hole  U1520A, we can run

```
$ wc-l *U1520A*.csv
 407 372-U1520A_cali-nscope.csv
 407 372-U1520A_den-nscope.csv
3402 372-U1520A_gr-gvr.csv
2034 372-U1520A_gr-nscope.csv
 692 372-U1520A_misc-gvr.csv
 399 372-U1520A_por-nscope.csv
 420 372-U1520A_res-atten-nscope.csv
 692 372-U1520A_res-gvr.csv
 420 372-U1520A_res-phase-nscope.csv
 422 372-U1520A_tp-nscope.csv
 421 372-U1520A_vel-sscope.csv
9716 total
```

here the flag `-l` asks `wc` to show only the number of lines.


#### Organizing files

Now that we know how to move things around and how to operate on multiple files, it would be a good idea to organize our data a bit. We see that we have data from two different expeditions (372 and 376) and that expedition 372 has three different holes. Let's first create one directory for each expedition and one subdirectory for each hole and then combine `mv` and wildcards to 
sort the files into their respective subdirectories. 

```
$ pwd
/Users/bia/work/classes/GPGN268/coursework-villasboas/ds01-well-log/iodp-logging-data
```

```
$ mkdir EXP372 EXP376
$ cd EXP372
$ mkdir U1520A U1517A U1520B
$ mv 372*U1520A*.csv EXP372/U1520A
```

Similarly for the other holes.

#### Combining multiple commands

We learned that we can use `ls` to list the contents of a directory and that the flag `-1` (the number one, not the letter "l") prints one file per line. So what if we wanted to count how many files are in a given directory?

We know that `wc -l` counts the number of lines in a given input and we have used it to count the lines in a file, but what if we could use it to count the number of lines in the output from `ls -1`?
Shell lets us combine multiple commands using "pipes".

```
$ ls -1 U1520A | wc -l
12
```

The vertical bar, `|`, between the two commands is called a pipe. It tells the shell that we want to use the output of the command on the left as the input to the command on the right.

Let's try to use pipes with other commands.

```
$ ls U1520A | head -n 2
```

Here shell will execute the command `head  -n 2` on the output of the command `ls U1520A`.  Now let's try again to use wildcards to count the lines on all files of hole U1520A

```
$ wc U1520A/*.csv
```

Note that the output is sorted based on the name of the files, not the number of lines. If we wanted to sort the output such that the file with the least number of lines is first, we can combine `wc` and the command `sort`

```
$ wc U1520A/*.csv | sort
```

and to reverse the order, we can try

```
$ wc U1520A/*.csv | sort -r
```

#### Deleting is forever

The Unix command we’ll use for deleting is `rm` (short for ‘remove’).

⚠⚠️⚠️ **The Unix shell doesn’t have a trash bin** that we can recover deleted files from. Instead, when we delete files, they are unlinked from the file system so that their storage space on disk can be recycled. Deleting with the command `rm` is FOREVER.

Let's try this on the file `iodp-usio-acronyms.html`

```
$ cd ~/work/classes/GPGN268/coursework-villasboas/ds01-well-log/iodp-logging-data
$ ls -F
```

```
$ rm iodp-usio-acronyms.html
$ ls -F
```

If you look in your system's trash using the graphical interface, you won't see iodp-usio-acronyms.html there. It's gone. 

In our last lecture, we created a directory called `research`, but we haven't really done anything with it, so let's delete it. 

```
$ cd ~/work
$ ls -F
```

```
$ rm research
rm: cannot remove `thesis`: Is a directory
```

This happens because `rm` by default only works on files, not directories. To delete directories, we need to tell `rm` to remove everything in the directory, then the directory itself (even if the directory is empty).  We can do this with the [recursive](https://en.wikipedia.org/wiki/Recursion) option for `rm`:

```
$ rm -r research
```

#### 🔎 Key Points
-   `rm [path]` removes (deletes) a file.
-   `*` matches zero or more characters in a filename, so `*.txt` matches all files ending in `.txt`.
- wc counts lines, words, and characters in its inputs.
- cat displays the contents of its inputs.
- sort sorts its inputs.
- head displays the first 10 lines of its input.
- tail displays the last 10 lines of its input.
