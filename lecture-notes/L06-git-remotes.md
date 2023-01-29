# Remotes in GitHub

#### 🎯 Learning Objectives: 
-   Explain what remote repositories are and why they are useful.
-   Push to or pull from a remote repository.

Last lecture we learned how to initialize a local repository and track files using git. The last thing we did was to create a remote repository on GitHub and try to connect that with our local repository.  Since we did this at the very end of class, we didn't have time to configure things properly.

####  SSH Background and Setup

Before you can connect to a remote repository, we needs to set up a way for your computer to authenticate with GitHub so it knows it’s you trying to connect to your remote repository.

We are going to set up the method that is commonly used by many different services to authenticate access on the command line. This method is called Secure Shell Protocol (SSH). SSH is a cryptographic network protocol that allows secure communication between computers using an otherwise insecure network.

SSH uses what is called a key pair. This is two keys that work together to validate access. One key is publicly known and called the public key, and the other key called the private key is kept private. Very descriptive names.

You can think of the public key as a padlock, and only you have the key (the private key) to open it. You use the public key where you want a secure method of communication, such as your GitHub account. You give this padlock, or public key, to GitHub and say “lock the communications to my account with this so that only computers that have my private key can unlock communications and send git commands as my GitHub account.”

What we will do now is the minimum required to set up the SSH keys and add the public key to a GitHub account.

We will run the list command to check what key pairs already exist on your computer.

```
ls -al ~/.ssh
```

Your output is going to look a little different depending on whether or not SSH has ever been set up on the computer you are using.

If you have not set up SSH on your computer, so his output is

```
ls: cannot access '/c/Users/Blaster/.ssh': No such file or directory
```

If SSH has been set up on the computer you’re using, the public and private key pairs will be listed. The file names are either `id_ed25519`/`id_ed25519.pub` or `id_rsa`/`id_rsa.pub` depending on how the key pairs were set up.  

#### Create an SSH key pair

To create an SSH key pair we will use this command, where the `-t` option specifies which type of algorithm to use (don't worry about the details)

```
$ ssh-keygen -t ed25519
```

If you are using a legacy system that doesn’t support the Ed25519 algorithm, use: `$ ssh-keygen -t rsa -b 4096 

```
Generating public/private ed25519 key pair.
Enter file in which to save the key (/c/Users/Blaster/.ssh/id_ed25519):
```

We want to use the default file, so just press Enter.

```
Created directory '/c/Users/Blaster/.ssh'.
Enter passphrase (empty for no passphrase):
```

Now, it will prompt you for a passphrase.  Be sure to use something memorable or save your passphrase somewhere, as there is no “reset my password” option.

```
Enter same passphrase again:
```

After entering the same passphrase a second time, we receive the confirmation

```
Your identification has been saved in /c/Users/Blaster/.ssh/id_ed25519
Your public key has been saved in /c/Users/Blaster/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:SMSPIStNyA00KPxuYu94KpZgRAYjgt9g4BA4kFy3g1o
The key's randomart image is:
+--[ED25519 256]--+
|^B== o.          |
|%*=.*.+          |
|+=.E =.+         |
| .=.+.o..        |
|....  . S        |
|.+ o             |
|+ =              |
|.o.o             |
|oo+.             |
+----[SHA256]-----+
```

The “identification” is actually the private key. You should never share it. The public key is appropriately named. The “key fingerprint” is a shorter version of a public key.

Now that we have generated the SSH keys, we will find the SSH files when we check.

```
ls -al ~/.ssh
```

```
drwxr-xr-x 1 Blaster 197121   0 Jul 16 14:48 ./
drwxr-xr-x 1 Blaster 197121   0 Jul 16 14:48 ../
-rw-r--r-- 1 Blaster 197121 419 Jul 16 14:48 id_ed25519
-rw-r--r-- 1 Blaster 197121 106 Jul 16 14:48 id_ed25519.pub
```

#### Copy the public key to GitHub
Now we have a SSH key pair and we can run this command to check if GitHub can read our authentication.

```
ssh -T git@github.com
```

```
The authenticity of host 'github.com (192.30.255.112)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? y
Please type 'yes', 'no' or the fingerprint: yes
Warning: Permanently added 'github.com' (RSA) to the list of known hosts.
git@github.com: Permission denied (publickey).
```

Right, we forgot that we need to give GitHub our public key!

First, we need to copy the public key. Be sure to include the `.pub` at the end, otherwise you’re looking at the private key.

```
cat ~/.ssh/id_ed25519.pub
```

```
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIDmRA3d51X0uu9wXek559gfn6UFNF69yZjChyBIU2qKI 
```

Now, going to GitHub.com, click on your profile icon in the top right corner to get the drop-down menu. Click “Settings,” then on the settings page, click “SSH and GPG keys,” on the left side “Account settings” menu. Click the “New SSH key” button on the right side. Now, you can add the title (such as " Blaster's laptop" so you can remember where the original key pair files are located), paste your SSH key into the field, and click the “Add SSH key” to complete the setup.

Now that we’ve set that up, let’s check our authentication again from the command line.

```
$ ssh -T git@github.com
```

```
Hi Blaster! You've successfully authenticated, but GitHub does not provide shell access.
```

Good! This output confirms that the SSH key works as intended. We are now ready to push our work to the remote repository.

#### Reset the remote origin

We had set up a remote origin last time. We will remove it now to make sure we're all doing the same thing.

```
$ git remote rm origin
```

```
$ git remote add origin git@github.com:Blaster/resume.git
```

```
$ git push
```
