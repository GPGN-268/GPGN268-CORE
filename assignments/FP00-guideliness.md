# 🌎 GPGN268 Final Project Guidelines

## Overview

The final project is an essential component of this course. It provides an opportunity for you and your group to independently scope and explore a topic of interest, apply some of the concepts and approaches that we’ve covered during the course to a real-world research problem, and solidify your understanding of the material. The hope is that you can share what you learned with your classmates, and then proudly post your final project repository on your GitHub page to share with the world (and future employers).

The final project seeks to assess your ability to do the following tasks:

-   Find, process, visualize, analyze, and interpret geophysical data from a chosen topic;
-   Use Unix commands to work with files and directories;
-   Identify the data format(s) from the chosen dataset(s) and the best tools to handle them;
-   Construct complete, well-structured programs in Python;
-   Work in a team to solve a geophysical problem and collaborate on the project through GitHub;
-   Practice reproducible research through version control, documentation, and metadata aggregation.

## Expectations and Deliverables

The goal here is the same as with any science project: to use the data to investigate a scientific question or hypothesis. In order to succeed on the project, you will have to draw on your experience _outside_ our class, from your science-focused classes or independent research, in order to define a scientifically interesting question. It is also acceptable (and encouraged) to use this project to reproduce the results from a published study that you find interesting.

Whatever you choose, you should _clearly define a hypothesis or scientific question that you aim to investigate with your analysis_. This will determine what you have to do.


### ✅ Technical Requirements

####  General Requirements

- The results of your analysis will be figures. **Beautiful** figures that clearly provide answers to your question/hypothesis. Your main notebook should contain at least 4 and no more than 8 figures. All figures must have titles, clearly labeled axes, [informative colormaps](https://jakevdp.github.io/blog/2014/10/16/how-bad-is-your-colormap/) / colorbars, multiple panels, and legends, when appropriate. 
- All your code must be well-documented with comments and functions when appropriate.  I expect you to use expressive variable names and proper formatting. 

#### Specific requirements

A final project repository with a remote hosted on GitHub. The repository should contain:

1.  A `README.md file` containing:
	- Project Title
	-   Name(s) and GitHub handles of all team members
	-   Project summary
	- How to use this repository
	-   Introduction including background information, problem statement, objective(s), and any other relevant information, images/tables, references, etc.
	-   List of all datasets you will use (with Markdown-formatted links to the specific data sources)
	-   Tools and packages that are used in the project (with links)
	-   Project methodology/approach
	-   Summary of the results.
	- Contribution statement describing the role of each group member
	-   References
2.  An `enviroment.yml` file with a proper environment name and list of all libraries needed for your project (see example [here](https://github.com/GPGN-268/GPGN268-CORE/blob/main/environment.yml))
3. A directory tree for your project that follows [best practices in scientific computing](https://github.com/GPGN-268/GPGN268-CORE/blob/main/lecture-notes/L03-files-directories.md)
4. All code necessary to reproduce your analysis (Bash scripts, python scripts, auxiliary Jupyter notebooks) + a main Jupyter notebook containing your results and figures.

### 📽️ Record your presentation

 Each group will prepare and record a ~10-minute presentation/demo in Week 15. You can use the software of your choice to do this, but I recommend using Zoom and following [these instructions](https://library.gwu.edu/sites/default/files/2023-06/How%20to%20Record%20a%20Video%20Presentation%20using%20Zoom.pdf). All group members should have their video on during the recording (this content will not be shared outside of the class unless you wish to do so).

-  All group members are expected to contribute to the presentation.
-   Format is flexible: can be slides (not necessary), scrolling through notebook(s), scrolling through markdown files
	-   If using slides, please save them as a pdf and push the slides to your final project repo. 
-   Please consider the following points when preparing your presentation:
	- Introduce the topic of your project and your group's motivation to choose this particular topic.
	- State your research question (what you aimed to achieve) and explain why it is important.
   	- Describe your dataset and explain the methods that you used to collect data, including the type of data collected, how you collected it, and any challenges you encountered during the process.
	- Describe how you analyzed your data and what tools and techniques you used to do so.
	- Present your findings in a clear and concise manner, using figures where appropriate.
	- Discuss the implications of your findings and how they relate to your original question/hypothesis.
	- Go over any limitations or weaknesses in your approach.
	- Summarize your main findings and their significance.
 	- Suggest areas for future research that could build on your findings.
	- Acknowledgments: Thank those who have supported your group project if applicable (any peers, friends, mentors, other faculty, etc.)
	- **Have fun!** This is your opportunity to showcase all the hard work you have put into your research project.

### ⬆️ Upload your recording to Canvas by April 25th, 11:59 PM

-   After you have your .mp4 file with your presentation recording, head to the [Canvas discussion board](https://elearning.mines.edu/courses/63978/discussion_topics) and search for the topic corresponding to your group. Then, upload your video to the discussion as a file attachment (note that only the group leader needs to do this)   
-   After you upload your video presentation, please enable read access on your final project repo on GitHub, so others in the class can see your great work, and learn from what you’ve done!
	-   Open the “Settings” tab near the top of your repo  
	-   Select “Manage Access” on the left side
	-   Click the green “Invite teams or people”
	-   Type `GPGN268-students` in the search bar and select
	-   Use the default Read access and click the green button to proceed
	-   I recognize that this may feel a little uncomfortable, especially if you didn’t have as much time as expected or don’t feel your repo is “finished.” It’s OK! We’re all in the same boat and projects like this are never truly finished. See below for some additional thoughts, and please reach out if you would like to discuss.

### 🤙🏼 Join the conversation by April 29, 11:59 PM

-   I expect active engagement from the entire class. Part of your final project grade is based on participation asking questions and providing feedback to the other groups.
-   Each student should watch everyone's presentation and post questions (or provide constructive feedback) on the discussion board of at least three different projects. You will be randomly assigned to be the peer reviewer of 3 other groups. 
-   Group members should take turns answering the question and addressing the comments from their peers

### 📆 Final Project Submission (Due on Wednesday, May 3rd 11:59 PM)

-   Finalize your repository with notebooks, scripts, and documentation that incorporates the feedback you received from me, the TA, and your peers.        
-   Clean up your repository and make sure only the necessary material is there. You may create a directory called `dev` and move old or unused files there.
-   Update the section "How to use this repository" in the README with information about the notebooks used during processing and provide a clear indication of which notebooks contain the final results.
	-   The goal is to help someone who is unfamiliar with your project quickly find the good stuff!
-   Submit the GitHub URL for your final project repo on Canvas before midnight on Wednesday, May 1st. 

### 🚀 Optional: Share your amazing work!

You have two options - share with the world or only share with other students in the class. It’s up to you, but if you are comfortable sharing and there are no issues involving proprietary data, I suggest sharing with the world (colleagues, advisors, friends, family, and **future employers!**):

To make the repo public and share it with the world:
-   From the “Settings” tab, scroll all the way down to the `Danger Zone` and click “Change Visibility”
-   Select “Make Public” and type the repo name in the prompt
-   Proudly share the repo URL with others!

🛜 If **everyone** in your group agrees and would like to, we could have your final presentation uploaded to the GP YouTube channel (this could be used as a way to showcase your presentation skills to prospective employers)


