
### Generating an SSH key

1) Open Git Bash and enter  `pwd` . This command will show us the current working directory, which is the directory you are currently located in within the terminal. 

Example: 

![pwd.png](Images%2Fpwd.png)


2) You then want to see all the files and directories, including hidden ones in the current directory . You do this by entering  `ls - a`  

We want to access the .ssh folder, this folder is where we want to generate and store SSH key pair. 

Example:

![ls_a.png](Images%2Fls_a.png)


3) We want to now access the .ssh directory, we do this by entering `cd .ssh` on our terminal. 

Example:

![cd_ssh.png](Images%2Fcd_ssh.png)


4) Once you have entered the command above, you will know you are in the .ssh directory as it should show  `~/.ssh` on your terminal. We then need to enter `ssh-keygen -t rsa -b 4096 -C "prismikagurung1@gmail.com"` in order to generate an RSA key pair. 

***command explained:*** 

`ssh-keygen` - this command is for generating SSH keys. 

`-t rsa` - This specifies the type of key to generate, RSA is a widely used public key. 

`-b 4096` - This sets the key length to 4096 bits. 

`-C` - This allows you to add a comment to the key. 

When we enter this command, it will ask us to enter a file in which to save the key, this is where we want to name the key, I have named mine “**GitHub_test”**. It then asks us if we want to enter passphrase, I have left this empty by pressing enter and confirming by pressing enter again. It will then confirm that a key pair has been generated for us. 

Example: 

![key_pair_generated.png](Images%2Fkey_pair_generated.png)

5) We can double-check that the key pairs have been created by entering `ls` in the current `.ssh` directory we are in. It should show a private and a .pub keys. 

Example: 

![ls_keypair.png](Images%2Fls_keypairs.png)

### Adding SSH key to GitHub account.

6) We can now add our public SSH key to our GitHub account, so we can commit and push our repository using SSH. On Git Bash we can print out our public key by entering `cat github_test.pub` . This will print out our public key, we can copy and paste this on your GitHub account. 

Example: 

![cat_sshkey.png](Images%2Fcat_sshkey.png)

We go into our **GitHub account > settings > SSH & GPG** 

![github_settings.png](Images%2Fgithub_settings.png)

Add new SSH key

![ssh_key.png](Images%2Fssh_key.png)

And we finally copy and paste our public SSH key from Git Bash. The title can be the name of your SSH key. 

![ssh_key_github.png](Images%2Fssh_key_github.png)

It should now show that your SSH key has been generated and saved on GitHub. 

![key_saved.png](Images%2Fkey_saved.png)

### Pushing out local repository to GitHub using SSH

7) After making a new repository on our GitHub, we also need to initialise a new Git repository in our local directory. 
We do this by entering `git init` in our git bash terminal on our Pycharm.
```Prismika@Pris MINGW64 ~/PycharmProjects/GitHub_SSH
$ git init
Initialized empty Git repository in C:/Users/Prismika/PycharmProjects/GitHub_SSH/.git/
```
8) Now we will need to add an SSH agent, the SSH agent manages your SSH key and holds our private keys in memory allowing us to authenticate with remote servers without having to enter your passphrase every time. In order to run the SSH agent we enter  `eval $(ssh-agent -s)` and it will assign you an agent. PID stands for Process Identifier. 
- `eval` - execute the output of the command` $(...)` in the current shell environment.
- `ssh-agent -s:` starts the SSH agent and prints out the necessary environment variables that need to be set. 

![agent.png](Images%2Fagent.png)


9) After running this command, we will need to add our SSH private key to the agent using `ssh-add ~/.ssh/github_ssh`. Replace `~/.ssh/github_ssh` with the path to your private key. 
It should show that the Identity has been added as shown below:
- `ssh-add:` add private keys to the SSH agent.
- `~/.ssh/github_ssh` - This is the path to the private key file you want to add.

![assigning_sshkey_to_agent.png](Images%2Fassigning_sshkey_to_agent.png)


10) Using the command `ssh -T git@github.com 
` enables us to test our SSH connection to GitHub. If everything is set up correctly so far, GitHub will respond with a message indicating successful authentication as shown below.

![authenticating_ssh_github.png](Images%2Fauthenticating_ssh_github.png)

11) We will then need to add our remote repository named origin in our local git. We can do this by entering the command `git remote add origin git@github.com:Pxxmie/AWS_and_Cloud_Computing.git`
![git_remote_add_origin.png](Images%2Fgit_remote_add_origin.png)


12) Finally, we need to make sure Git will push the commits from your local 'main' branch to the 'main' branch in the 'origin' remote repository. We do this by entering the command `git push -u origin main`. In the picture below, we can see that a new branch has been created and all committed files has been pushed to the remote repository. 
<br>
![git push.png](Images%2Fgitpush.png)

##### Useful Git Commands 

-  `git init ` - Initialise the local directory as a Git repository.
- `git status` - used to display the current state of the repository.
- `git add .` - Stage the files for the first commit by adding them to the local repository.
- `git commit -m "   "` - Create a new commit in your Git followed my `-m` which stands for message. 
- `git push / git push -u origin main `- Pushes out committed local repository to remote repository.
- `git log` - see the logs of all the commits made.
- `git remote -v` - Viewing git remote configurations
