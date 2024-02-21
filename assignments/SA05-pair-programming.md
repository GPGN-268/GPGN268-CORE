
# SA05 - Pair programming 

### Task 1
- Create a repository in **your own github** (not the GPGN268 organization) called `lastname-pair-programming`
- Clone the empty repository to the root GPGN268 directory. Make sure you use the URL of your own repository, by checking the `SSH` option. The address should start with `git@github.com`. Remember you need to do that using GitBash if you are on Windows.

```
$ cd ~/work/classes/GPGN268
$ git clone git@github.com:biavillasboas/villasboas-pair-programming.git
```


- On GitHub, go to your repository settings and add your pair as a collaborator (if you haven't been paired with a partner during class, email me ASAP)


<img width="1373" alt="Screenshot 2023-02-16 at 2 30 57 PM" src="https://user-images.githubusercontent.com/2079352/219497880-d0fb084f-6ce5-43f7-9be5-52c10cc5aa53.png">


<img width="1400" alt="Screenshot 2023-02-16 at 2 31 10 PM" src="https://user-images.githubusercontent.com/2079352/219497894-318e0136-ac4c-41ac-9596-e602d14c51bf.png">


<img width="1295" alt="Screenshot 2023-02-16 at 2 31 30 PM" src="https://user-images.githubusercontent.com/2079352/219497919-f5076cd2-a53d-4aff-9f5a-a183ae4687f0.png">


- After you and your collaborator add each other to your respective repositories, you should get an invitation by email (or by clicking on the bell icon on GitHub). After you accept the invitation, you should be able to see each other's repositories. 


### Task 2

- Back to your Anaconda prompt (or terminal on Mac), navigate to your newly created repository and launch juypter lab

```
$ cd ~/work/classes/GPGN268/villasboas-pair-programming
$ jupyter lab
```

- Choose "Python File" in the Jupyter Lab launcher. This will create an empty text file that you will use to write your code. Rename the file to `pair_programming.py`. Open a new tab in Jupyter Lab and choose "Console - Python 3". Then, re-arrange your windows to have the Python script and the console side-by-side.

<img width="1118" alt="python-console" src="https://github.com/GPGN-268/GPGN268-CORE/assets/2079352/a5fee41b-bf8a-4309-adee-6e1cace2416a">

<img width="1440" alt="side-by-side" src="https://github.com/GPGN-268/GPGN268-CORE/assets/2079352/3733a0b0-b719-4f51-ab32-6b6e2586a67e">


- On your newly created Python file (pair_programming.py), write a function to do what is on the prompt below based on the prompt number that was assigned to you (see the table).
- Document your function such that someone else can understand what is going on (but don't write tests for it). You should youse the Python prompt to execute your code and check if it's working.
- When you're done and ready to get feedback from your partner, save your code, shutdown jupyter lab, add your .py file to git, commit your changes, and push it to GitHub. **Make sure your commit message tells your partner that you're ready for feedback**. For example, if I'm working with Jordan:

```
$ git add pair_programming.py
$ git commit -m "Add notebook ready for feedback from @Jordan"
$ git push
```


##### Function prompts 
1. Takes two values (feet and inches) and converts to meters
2. Changes coordinates from polar to Cartesian
3. Offsets the mean of a given array to match a given value
4. Takes an input array and returns values scaled to lie in the range of 0.0 to 1.0. 



| Student          | Prompt # | Student             | Prompt # |
| ---------------- | -------- | ------------------- | -------- |
| Colin Thomas     | 1        | Kaitlyn Manalili    | 2        |
| Katie Gonzalez   | 3        | Seth Reichelt       | 1        |
| Emily Pearson    | 1        | Jude Lowe           | 2        |
| Nathan Sedmak    | 3        | Peyton Chandler     | 4        |
| Renee Fischer    | 3        | Lucas Holt          | 4        |
| Max Ercolani     | 4        | Jackson Howard      | 1        |
| Grey Garner      | 4        | Finley Wolff        | 3        |
| Kailey Dougherty | 2        | Julia Berglind      | 1        |
| Bianca Riebe     | 3        | Wade Kahl           | 1        | 
| Olivia Wills     | 2        | Jimena Garciaprieto | 1        |
| Eliza Ross       | 1        | Anna Melega         | 2        |
| Callum Hood-Cree | 3        | Jack Logan          | 4        |
| Jack Dollar      | 3        | TA                  | 1        |



### Task 3
- Accept the invitation from your partner, go to their repository on GitHub, and check the commit messages on GitHub to see if their work is ready for your feedback.
- On the GitHub page of your partner's repository, click on `code`, check the option `SSH`, copy the link.
- On your terminal, navigate to the main GPGN268 directory and clone your partner's repository
```
cd ~/work/classes/GPGN268
git clone git@github.com:your-pair-username/your-pair-lastname-pair-programming.git
```

- Navigate to the cloned repo and launch jupyter lab.
- You will see your partner's function
- Check the documentation. Write comments with your feedback (what looks good, what could be improved)
- Using a cell below your partner's work, write a function that tests your partner's function with at least two tests 
- Save your work. Shut down jupyter lab. Add and commit your changes. Push it back to your partner on GitHub

```
$ cd ~/work/classes/GPGN268/your-pair-lastname-pair-programming
$ git add pair_programming.py
$ git commit -m "Add feedback and test function"
$ git push
```
