# Lecture 02 – Intro to bash
#### 🎯 Learning Objectives: 
-   Explain the similarities and differences between a file and a directory.
- Translate an absolute path into a relative path and vice versa
- Run `Bash` commands to complete the following tasks:
	-   print the current working directory (`pwd`)  
	-   navigate between directories on your computer (`cd`)  
	-   create new directories (`mkdir`)  
	-   print a list of files and subdirectories within directories (`ls`)  

#### 🖥️ Introducing the Shell

Modern computers have graphical user interfaces (known as GUIs) that make it easy to perform tasks. While the visual aid of a GUI makes it intuitive to learn, this way of delivering instructions to a computer scales very poorly. Imagine the following task: for a literature search, you have to copy the third line of one thousand text files in one thousand different directories and paste it into a single file. Using a GUI, you would not only be clicking at your desk for several hours, but you could potentially also commit an error in the process of completing this repetitive task. This is where we take advantage of the Unix shell. The Unix shell is both a **command-line interface** (CLI) and a scripting language, allowing such repetitive tasks to be done automatically and fast. With the proper commands, the shell can repeat tasks with or without some modification as many times as we want. Using the shell, the task in the literature example can be accomplished in seconds

The shell is a program where users can type commands. With the shell, it’s possible to invoke complicated programs like climate modeling software or simple commands that create an empty directory with only one line of code. The most popular Unix shell is Bash (the Bourne Again SHell — so-called because it’s derived from a shell written by Stephen Bourne). Bash is the default shell on most modern implementations of Unix and in most packages that provide Unix-like tools for Windows.

Using the shell will take some effort and some time to learn. While a GUI presents you with choices to select, CLI choices are not automatically presented to you, so you must learn a few commands like new vocabulary in a language you’re studying. However, unlike a spoken language, a small number of “words” (i.e. commands) gets you a long way, and we’ll cover those essential few today.

The grammar of a shell allows you to combine existing tools into powerful pipelines and handle large volumes of data automatically. Sequences of commands can be written into a _script_, improving the reproducibility of workflows.

In addition, the command line is often the easiest way to interact with remote machines and supercomputers. Familiarity with the shell is near essential to run a variety of specialized tools and resources including high-performance computing systems. As clusters and cloud computing systems become more popular for scientific data crunching, being able to interact with the shell is becoming a necessary skill. We can build on the command-line skills covered here to tackle a wide range of scientific questions and computational challenges.

Let’s get started.

#### Navigating files and directories

To get started, open a terminal using the "terminal" application on Mac or GitBash on Windows. When the shell is first opened, you are presented with a **prompt**, indicating that the shell is waiting for input. You will see something like this:

```
bia@dune:~$
```

The dollar sign is a **prompt**, which shows us that the shell is waiting for input. `bia` is my **username** and `dune` is my **hostname**.  We each have a different username and hostname (the name of the computer we are using), which may change depending on the machine you are using. From now on, we will use a `$` to indicate the prompt. Do not type the dollar sign and the space when typing commands (either from these notes or from other sources) – only type the commands that follow it. Also note that after you type a command, you have to press the Enter key to execute it.

To find out your username in general, you can use the command

```
$ whoami
bia
```


Next, let’s find out where we are by running a command called `pwd` (which stands for “print working directory”). At any moment, our **current working directory** is our current default directory, i.e., the directory that the computer assumes we want to run commands in unless we explicitly specify something else. Here, the computer’s response is `/Users/bia`, which is the **home directory** of the user named `bia`.

```
$ pwd
/Users/bia
```

To understand what a “home directory” is, let’s have a look at how the file system as a whole is organized. For the sake of this example, we’ll be illustrating the filesystem on a hypothetica Mines computer. After this illustration, you’ll be learning commands to explore your own filesystem, which will be constructed in a similar way, but not be exactly identical.

On a Mac computer, the filesystem looks like something this:

<img src="https://user-images.githubusercontent.com/2079352/212183620-865ab24c-fddd-4cff-89b6-c41353684770.gif" width=600>

At the top is the **root directory** that holds everything else. We refer to it using a slash character `/` on its own; this is the leading slash in `/Users/bia`.

Inside that directory are several other directories:  `Library` (for the software “libraries” used by different programs), `bin` (which is where some built-in programs are stored), `Users` (where users’ personal directories are located), `System` (system-wide configuration files), and so on.

**Windows users:** note that the `Terminal` uses forward slashes (`/`) to indicate directories within a path. This differs from the Windows File Explorer which uses backslashes (`\`) to indicate directories within a path. Your home directory might look something like `C:\Documents and Settings\nelle` or `C:\Users\nelle` depending on your Windows version.

Now let’s learn the command that will let us see the contents of our own filesystem. We can see what’s in our home directory by running `ls`, which stands for “listing”:

```
$ ls
Applications   Documents    Library    Music  Public
Desktop          Downloads    Movies   Pictures
```

(Again, your results may be slightly different depending on your operating system and how you have customized your filesystem.)

`ls` prints the names of the files and directories in the current directory in alphabetical order, arranged neatly into columns. We can make its output more comprehensible by using the **flag** `-F`, which tells `ls` to add a trailing `/` to the names of directories:

```
$ ls -F
Applications/		Library/		Public/
Desktop/		        Movies/		note-template.md
Documents/		    Music/
Downloads/		    Pictures/
```

`ls` has lots of other options. To find out what they are, we can type:

```
$ ls --help
```


### Exploring Other Directories

Not only can we use `ls` on the current working directory, but we can use it to list the contents of a different directory. Let’s take a look at our `Desktop` directory by running `ls -F Desktop`, i.e., the command `ls` with the `-F` **option** and the **argument**  `Desktop`. The argument `Desktop` tells `ls` that we want a listing of something other than our current working directory:

```
$ ls Desktop
attendance-20230109.csv seismo-files
inbox well-log-data
```

Your output should be a list of all the files and sub-directories in your Desktop directory. On many systems, the command line Desktop directory is the same as your GUI Desktop. Take a look at your Desktop to confirm that your output is accurate.

As you may now see, using a bash shell is strongly dependent on the idea that your files are organized in a hierarchical file system. Organizing things hierarchically in this way helps us keep track of our work: it’s possible to put hundreds of files in our home directory, just as it’s possible to pile hundreds of printed papers on our desk, but it’s a self-defeating strategy.

We can use `ls` to look at the content of subdirectories, by passing the path to the target diretory. For example, if we want to know the contents of `well-log-data`, we run:

```
$ ls Desktop/well-log-data
```

Another thing that we might want to do is to  actually change our location to a different directory, so we are no longer located in our home directory. The comand to change locations is `cd` followed by a directory name to change our working directory. `cd` stands for “change directory”, which is a bit misleading: the command doesn’t change the directory, it changes the shell’s idea of what directory we are in. The `cd` command is akin to double-clicking a folder in a graphical interface to get into a folder.

Let’s say we want to move to the `logging-resources` directory we saw above. We can use the following series of commands to get there:

```
$ cd Desktop
$ cd well-log-data
$ cd logging-resources
```

These commands will move us from our home directory into our Desktop directory, then into the `well-log-data` directory, then into the `ogging-resources` directory. You will notice that `cd` doesn’t print anything. This is normal. Many shell commands will not output anything to the screen when successfully executed. But if we run `pwd` after it, we can see that we are now in `/Users/bia/Desktop/well-log-data/logging-resources`.

If we run `ls -F` without arguments now, it lists the contents of `/Users/bia/Desktop/well-log-data/logging-resources`, because that’s where we now are.

We now know how to go down the directory tree (i.e. how to go into a subdirectory), but how do we go up (i.e. how do we leave a directory and go into its parent directory)? We might try the following:

```
$ cd well-log-data
cd: no such file or directory: well-log-data
```

But we get an error! Why is this?

With our methods so far, `cd` can only see sub-directories inside your current directory. There are different ways to see directories above your current location; we’ll start with the simplest.

There is a shortcut in the shell to move up one directory level that looks like this:

```
$ cd ..
```

`..` is a special directory name meaning “the directory containing this one”, or more succinctly, the **parent** of the current directory. Sure enough, if we run `pwd` after running `cd ..`, we’re back in `/Users/bia/Desktop/well-log-data/`:

```
$ pwd
/Users/bia/Desktop/well-log-data/
```

The special directory `..` doesn’t usually show up when we run `ls`. If we want to display it, we can add the `-a` option to `ls -F`:

```
$ ls -F -a
./  ../  logging_data_figure.pdf   logging_methods.pdf
```

`-a` stands for ‘show all’ (including hidden files); it forces `ls` to show us file and directory names that begin with `.`, such as `..` (which, if we’re in `/Users/bia`, refers to the `/Users` directory). As you can see, it also displays another special directory that’s just called `.`, which means ‘the current working directory’. It may seem redundant to have a name for it, but we’ll see some uses for it soon.

Note that in most command line tools, multiple options can be combined with a single `-` and no spaces between the options: `ls -F -a` is equivalent to `ls -Fa`.

These three commands are the basic commands for navigating the filesystem on your computer: `pwd`, `ls`, and `cd`. Let’s explore some variations on those commands. What happens if you type `cd` on its own, without giving a directory?

```
$ cd
```

How can you check what happened? `pwd` gives us the answer!

```
$ pwd
/Users/bia
```

It turns out that `cd` without an argument will return you to your home directory, which is great if you’ve got lost in your own filesystem.

Let’s try returning to the `logging-resources` directory from before. Last time, we used three commands, but we can actually string together the list of directories to move to `exercise-data` in one step:

```
$ cd Desktop/well-log-data/logging-resources
```

Check that we’ve moved to the right place by running `pwd` and `ls -F`.

If we want to move up one level from the data directory, we could use `cd ..`. But there is another way to move to any directory, regardless of your current location.

So far, when specifying directory names, or even a directory path (as above), we have been using **relative paths**. When you use a relative path with a command like `ls` or `cd`, it tries to find that location from where we are, rather than from the root of the file system.

However, it is possible to specify the **absolute path** to a directory by including its entire path from the root directory, which is indicated by a leading slash. The leading `/` tells the computer to follow the path from the root of the file system, so it always refers to exactly one directory, no matter where we are when we run the command.

This allows us to move to our `well-log-data` directory from anywhere on the filesystem (including from inside `logging-resources`). To find the absolute path we’re looking for, we can use `pwd` and then extract the piece we need to move to `well-log-data`.

```
$ pwd
/Users/bia/Desktop/well-log-data/logging-resources
```


```
$ cd /Users/bia/Desktop/well-log-data/
```

Run `pwd` and `ls -F` to ensure that we’re in the directory we expect.

### Two More Shortcuts

1. The shell interprets the character `~` (tilde) at the start of a path to mean “the current user’s home directory”. For example, if my home directory is `/Users/bia`, then `~/Desktop` is equivalent to `/Users/bia/Desktop`. This only works if it is the first character in the path.

2. Another shortcut is the `-` (dash) character. `cd` will translate `-` into _the previous directory I was in_, which is faster than having to remember, then type, the full path. This is a _very_ efficient way of moving back and forth between directories. The difference between `cd ..` and `cd -` is that the former brings you _up_, while the latter brings you _back_. You can think of it as the _Last Channel_ button on a TV remote.

### Tab Completion

Typing the full path to directories and files can be slow and annoying. Fortunately, we have “tab completion” to help us. From your home, try typing `cd De` and then press the `<tab>`. The system will try to “auto complete” your command. Pressing tab twice brings up a list of all the files, and so on. This is called **tab completion**, and we will see it in many other tools as we go


### 🔎  Key Points:

-   “The file system is responsible for managing information on the disk.”
-   “Information is stored in files, which are stored in directories (folders).”
-   “Directories can also store other directories, which forms a directory tree.”
-   “`cd path` changes the current working directory.”
-   “`ls path` prints a listing of a specific file or directory; `ls` on its own lists the current working directory.”
-   `pwd` prints the user’s current working directory.
-   `whoami` shows the user’s current identity.
-   `/` on its own is the root directory of the whole file system.
-   A relative path specifies a location starting from the current location.
-   An absolute path specifies a location from the root of the file system.
-   Directory names in a path are separated with `/` on Unix, but `\` on Windows.
-   `..` means "the directory above the current one"; `.` on its own means ‘the current directory’.
-   Most files’ names are `something.extension`. The extension isn’t required, and doesn’t guarantee anything, but is normally used to indicate the type of data in the file.
-   Most commands take options (flags) which begin with a ‘-‘.


*These notes combine material from the [Earth and Environmental Data Sciences Book](https://earth-env-data-science.github.io/LICENSE.html), [Software Carpentry Lessons](https://software-carpentry.org/lessons/), and the [Earth Data Lab](https://www.earthdatascience.org) courses, all licensed under the [Creative Commons Attribution-ShareAlike](https://creativecommons.org/licenses/by-sa/4.0/) license. All contents Tin these organization are under the same license.* 
