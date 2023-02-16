
# SA05 - Pair programming 

### Task 1
- Create a repository in **your own github** (not the GPGN268 organization) called `lastname-pair-programming`
- Clone the empty repository to the root GPGN268 directory. Make sure you use the URL of your own repository, by checking the `SSH` option. The address should start with `git@github.com`

```
$ cd ~/work/classes/GPGN268
$ git clone git@github.com:biavillasboas/villasboas-pair-programming.git
```


- On GitHub, go to your repository settings and add your pair as a collaborator (if you haven't been paired with a partner during class, email me ASAP)


<img width="1373" alt="Screenshot 2023-02-16 at 2 30 57 PM" src="https://user-images.githubusercontent.com/2079352/219497880-d0fb084f-6ce5-43f7-9be5-52c10cc5aa53.png">


<img width="1400" alt="Screenshot 2023-02-16 at 2 31 10 PM" src="https://user-images.githubusercontent.com/2079352/219497894-318e0136-ac4c-41ac-9596-e602d14c51bf.png">


<img width="1295" alt="Screenshot 2023-02-16 at 2 31 30 PM" src="https://user-images.githubusercontent.com/2079352/219497919-f5076cd2-a53d-4aff-9f5a-a183ae4687f0.png">


- After you and your collaborator add each other to your respective repositories, you should get an invitation by email (or clicking on the bell icon on GitHub). After you accept the invitation, you should be able to see each others repositories. 


### Task 2

- Back to your terminal, navigate to your newly created repository and launch juypter lab

```
$ cd villasboas-pair-programming
$ jupyter lab
```

- Create a new notebook and rename it to `pair-programming.ipynb`

- On your newly created notebook, write a function to do what is on the prompt below based on the prompt number that was assigned to you (see the table). Note that names are side-by-side on the table just so things fit more snuggly – this is not necessarily your programming pair.
- Document your function such that someone else can understand what is going on (but don't write tests for it)
- When you're done and ready to get feedback from your partner, save your notebook, shutdown jupyter lab, add your notebook to git, commit your changes, and push it to GitHub. **Make sure your commit message tells your partner that you're ready for feedback**. For example, if I'm working with Seunghoo:

```
$ git add pair-programming.ipynb
$ git commit -m "Add notebook ready for feedback from @SeunghooKim"
$ git push
```


##### Function prompts 
1.  Takes two values (feet and inches) and converts to meters
2. Changes coordinates from polar to Cartesian
3.  Offsets the mean of a given data  to match a given value
4. Takes the input data and returns values scaled to lie in the range of 0.0 to 1.0. 



| Student        | Prompt # | Student            | Prompt # |
| -------------- | -------- | ------------------ | -------- |
| Chloe Locke    | 4        | Luke Mazza         | 3        |
| Nathan Bigelow | 2        | Sam Burton         | 2        |
| Thomas Ho      | 1        | Maile Corso        | 4        |
| Aaron Jimenez  | 4        | Paige Dompier      | 1        |
| Cash Cherry    | 3        | Madeline Pastuszek | 1        |
| Jalen Perkins  | 2        | Mia Jungman        | 2        |
| Aiden Hamre    | 1        | Anna Nichols       | 1        |
| Henry Truelson | 3        | Jackson Krieger    | 2        |
| Lexi Herr      | 4        | Jim Gabriel        | 2        |
| Grace Galvin   | 4        | Zach Mathias       | 3        |
| Duncan Byrne   | 3        | Kieran Yanaway     | 2        |



### Task 3
- Accept the invitation from your partner, got to their repository on GitHub, and check the commit messages on GitHub to see if their work is ready for your feedback.
- On the GitHub page of your partner's repository, click on `code`, check the option `SSH`, copy the link.
- On your terminal, navigate to the main GPGN268 directory and clone your partner's repository
```
cd ~/work/classes/GPGN268
git clone git@github.com:your-pair-username/your-pair-lastname-pair-programming.git
```

- Navigate to the cloned repo and launch jupyter lab.
- You will see your partner's fuction
- Check the documentation. Write comments with your feedback (what looks good, what could be improved)
- Using a cell below your partner's work, write a function that tests your partner's function with at least two tests 
- Save your work. Shut down jupyter lab. Add and commit your changes. Push it back to your partner on GitHub

```
$ cd ~/work/classes/GPGN268/your-pair-lastname-pair-programming
$ git add pair-programming.ipynb
$ git commit -m "Add feedback and test function"
$ git push
```
