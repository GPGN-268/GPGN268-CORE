---
date: 2023-01-17
course: GPGN268
tags: shell, bash, command-line
---

# Lecture 03 – Working With Files and Directories
#### 🎯 Learning Objectives: 
- Create a directory hierarchy that matches a given diagram.
- Move and rename specified files and/or directories.
- Describe machine and human readable names and the importance of using them to name directories and files.

#### Creating Directories

We now know how to explore files and directories, but how do we create them in the first place? In this lecture, we will learn about creating and moving files and directories. 

**Step one:** see where we are and what we already have.
```
$ pwd
/Users/bia
```
In my case, I'm in my `home` directory. If you are in a different directory, use `cd ~` to take you to your `home` and check it using `pwd`. Now, let see what is the content of our `home` directory.
```
$ ls -F
```

We will start by creating a directory called `work` in our `home `.

```
$ mkdir work
```

As you might guess from its name, `mkdir` means ‘make directory’. Since `work` is a relative path (i.e., does not have a leading slash, like `/what/ever/work`), the new directory is created in the current working directory:

```
$ ls -F
Applications/     Library/        Public/
Desktop/          Movies/			    note-template.md
Documents/        Music/			    work/
Downloads/        Pictures/
```

Note that `mkdir` is not limited to creating single directories one at a time. The `-p` option allows `mkdir` to create multiple directories with nested subdirectories in a single operation.

```
$ mkdir -p work/classes work/research 
```

```
$ ls -F work
classes/ research/
```

Now, following the filesystem illustrated below, let's create a directory named following the convention `coursework-your-last-name` under the directory `GPGN268` that is under the directory `classes`. 

![filesystem-coursework](https://user-images.githubusercontent.com/2079352/212988324-5974c58e-32b3-4e74-89b6-93c0f3927166.png)


```
$ mkdir -p work/classes/GPGN268/coursework-villasboas
```

The `-R` option to the `ls` command will list all nested subdirectories within a directory. Let’s use `ls -FR` to recursively list the new directory hierarchy we just created in the `work` directory:

```
$ ls -FR work
classes/	research/
work/classes:
GPGN268/
work/classes/GPGN268:
coursework-villasboas/
work/classes/GPGN268/coursework-villasboas:
work/research:
```

#### File and Directory Organization
###### Importance of Directory and File Names
As you create new directories and files on your computer,  use a carefully crafted naming convention that makes it easier for anyone (including **you**) to find things and also to understand what each file does or contains.

It is good practice to use file and directory names that are:

-   **Human readable**: use consistent, expressive names that clearly describe what the directory or file contains (e.g. code, data, outputs, figures).
-   **Machine readable**: avoid strange characters or white spaces. Instead of spaces, you can use `-` or `_` to separate words within the name to make them easy to read and parse.
-   **Sortable**: it is nice to be able to sort files to quickly see what is there and find what you need. For example, you can create a naming convention for a list of related directories or files (e.g. `L01-notes.md`, `L02-notes.md`, etc), which will result in sortable files.

If you need to refer to names of files or directories that have whitespace or another non-
alphanumeric character, you should surround the name in quotes ("").

###### The Structure of a Project 
Organize directories to make It easy to find data, code, and outputs.
- Store all of the files relevant to one project under a common `root` directory named after the project.
- Rather than saving a bunch of files into a single directory, consider using separate directories to store data, scripts, figures, and writing associated with the project. This makes it easier to navigate and find components of your projects.
- Document your workflow on a logbook file that records your progress in detail. These entries should be dated and contain as much detail as possible, including links,  images, and a record of your observations, conclusions, and ideas for future work.
- Record information about the data in a README file, where you specify what is the data, who downloaded the data files, from what URL, on what date, if any processing has been performed, etc.

In a few weeks, we will start working on "Data Stories", which will be small projects focusing on a specific type of geophysical data. Let's put the concepts above into practice using our first data story: well-logs. Since there will be many Data Stories, it would be nice to have a way to sort each project nicely. Let's navigate to our coursework directory and create the structure for our first project:

```
$ cd ~/work/classes/GPGN268/coursework-villasboas
$ pwd
```

```
$ mkdir ds01-well-log
```

The convention above will group all Data Story directories together (all start with the prefix " ds") and will sort them based on which project we started to work on first. The next thing that appears is an expressive name for the directory, that tell us what the project is about. For example, our second Data Story will be on global warming:

```
$ mkdir ds02-global-warming
```

🤔   Why do you think it's important to have a leading zero in the naming convention above? 

Now let's go ahead and create some subdirectories to organize our project.

```
$ cd ds01-well-log
$ mkdir data notebooks figures
```

Let's keep it like this for now. As we get started with our projects we might decide that is useful to create more directories.

###### 💭  What’s In a File Name?

You may have noticed that all of our data files are named ‘something dot something’, for example, `.csv`. This is just a convention: we can call a file `mycampaign` or almost anything else we want. However, most people use two-part names most of the time to help them (and their programs) tell different kinds of files apart. The second part of such a name is called the **filename extension** and indicates what type of data the file holds: `.txt` signals a plain text file, `.pdf` indicates a PDF document, `.md` is a Markdown text file, `.png` is a PNG image, and so on.

This is just a convention, albeit an important one. Files contain bytes: it’s up to us and our programs to interpret those bytes according to the rules for plain text files, PDF documents, configuration files, images, and so on.

Naming a PNG image of a whale as `whale.mp3` doesn’t somehow magically turn it into a recording of whale song, though it _might_ cause the operating system to try to open it with a music player when someone double-clicks it.

#### Moving and Renaming Files

In our last lecture, we downloaded some well-log data from Canvas and put it in a directory under `Desktop`. Now that we have a directory for our well-log project, it seems like it would make more sense for the well-log data to be there. How can we move  `~/Desktop/well-log-data` to our newly created project? For that, we will use the command ` mv` which stands for "move". The syntax is `$ mv source target`, where `source` and `target` can be given both in terms of the absolute path or the relative path.

For example

![filesystem-project](https://user-images.githubusercontent.com/2079352/212988583-9872cc72-e2ea-4a2b-8cc2-aaf273fccecb.png)


if `$ pwd` shows `$ ds01-well-log`, we can run

```
$ mv ~/Desktop/well-log-data data/
```


#### 🔎 Key Points
-   `mkdir [path]` creates a new directory.
-   `mv [old] [new]` moves (renames) a file or directory.  
- Expressive file and directory names are easier to navigate and remember their content/purpose
-   Most files names are `something.extension`. The extension isn’t required, and doesn’t guarantee anything, but is normally used to indicate the type of data in the file.
