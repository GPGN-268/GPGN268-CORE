
# Final project collaboration instructions

### 1. Create a project repository
- Chose a team leader to create a new private repository for your project _within the GPGN268 organization_ (can transfer to personal accounts later if desired). Go to (https://github.com/orgs/GPGN-268/repositories) and click the big green “New repository” button.
	- Use the prefix "SP2024-FPXX-", where "XX" is your group number (check it [here](https://docs.google.com/spreadsheets/d/1ucKjAmJEu4V3bwu5GuARyt5olO09e5xS_pTVfBl5xrc/edit#gid=1722963736)), followed by a descriptive name, for example:

		``SP2024-FP01-mars-seismo``

When you initialize the repository, select to include a [README.md](http://readme.md/) 

### 2. Add your team members as collaborators
- Following the same steps as in the [pair-programming exercise](https://github.com/GPGN-268/GPGN268-CORE/blob/main/assignments/SA05-pair-programming.md), search for your group members and add them as collaborators in the final project repository.

- If you're not the project lead, look out for an invitation to join the repository and accept it. 
- All group members should clone the repository to their local machine in the main `GPGN268` directory:

```
$ cd ~/work/classes/GPGN268
$ git clone your_group_repo_address
```

### 3. Create a project board
- The team leader should head to https://github.com/GPGN-268 and click on `projects`. 
- Select the green button "New project"
- Select "Board"
- Click on the project title, which will take you to the configuration page.
- Change the project name to the name of your project (doesn't have to match the repo name)
- Go to "Manage access" and add your team members


### Notes about collaborating on GitHub

Collaboration can be a bit more complicated with Jupyter notebooks (vs. standalone Python scripts/libraries), since running cells in the notebook will change execution count and output, even if the code and content appear identical. **Best practice is to avoid situations where two people are independently working on the same notebook**. 

**General recommendation** - split up the project into multiple smaller notebooks, and have each person work on different components. Avoid the long mega-notebook (like most of our labs), and instead structure your repo with a series of notebooks. For example, you could have one notebook that ingests files, reduces/manipulates the data (e.g., reprojection), then writes new files out to disk in “analysis-ready” format. Then a second notebook reads in those data and does some analysis, creates some plots, etc. If you can pass things back and forth between group members like this, you’ll avoid conflicts.

**Alternative recommendation**, each team member can create separate notebooks with different filenames that both live in the shared repo. When another team member does some work and commits their notebook to the shared repo, you can can pull changes, open their notebook, select relevant cells, copy and paste into your notebook. One simple option with this model is for each group member to create and maintain a subdirectory within the repo where they will stage and modify their own notebooks for their component of the project.


### 4. Prepare your README

The [README.md](http://readme.md/) file in your new repo will serve as the landing page for your project. You can continue to update as your project evolves, but for now, please prepare a basic project outline. I recommend that you review the markdown cheat sheet and use some basic headings, bulleted/numbered lists, and other formatting to organize your outline.

Please include the following (can combine and reorganize as necessary):

-   Project Title
-   Name(s) and GitHub handles of individual or team members
-   Short 1-2 sentence summary
-   Some introductory background information
-   Problem statement, question(s) and/or objective(s)
-   Datasets you will use (with links, if available)
-   Tools/packages you’ll use (with links)
-   Planned methodology/approach
-   Expected outcomes
-   Any other relevant information, images/tables, references, etc.
-   References

That may sound like a lot, but some of these items should only be 1-2 sentences or short lists. Consider this the start of your final report.

I would like to see **at least one commit from each group member** at this phase of the project, even if it is as simple as everyone using the GitHub interface to edit the [README.md](http://readme.md/) file and add their name. There are many approaches to collaborative group/team development using git/Github and no unique “right” way.

### 5. Work on your project!

-   Start early!
-   Use the best practices of scientific computing that we learned in class
	- Create subdirectories in your project (as needed) to store:    
	    - notebooks
	    - scripts
	    - figures
	    -  data (don't add this to git!) 
	    -  docs (if applicable) for any additional documentation, static images you want to include in notebooks or markdown files, etc.
-   Start adding and developing notebooks, code, markdown files, etc.
- Remember your git workflow:
	- Always pull before start working on your repository
	- Add **only** necessary files 
	- Commit and push often
	- There will be conflicts. Don't panic! Come talk to me.

## 📅 Final project Milestone (Due on 3/9)

The goal of the Milestone is to follow your progress on your final project and identify challenges that your group might be facing. By March 9, I would like to see:

1. An expanded version of the README file describing in detail:
	-   Problem statement, question(s) and/or objective(s)
	-   Datasets you will use (with links, if available)
	-   Tools/packages you’ll use (with links)
	-   Planned methodology/approach
	- Present or anticipated challenges
2.  A project board with large tasks broken down into standalone issues assigned to the respective group member(s) responsible for tackling it.
3. Evidence (in the form of commits, issues, comments) that all group members are participating
