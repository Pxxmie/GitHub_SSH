
### How to generate a SSH key.

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


4) Once you have entered the command above, you will know you are in the .ssh directory as it should show  `~/.ssh` on your terminal. We then need to enter `ssh-keygen -t rsa -b 4096 -C "prismikagurung1@gmail.com"` in order to generate a RSA key pair. 

***command explained:*** 

`ssh-keygen` - this command is for generating SSH keys. 

`-t rsa` - This specifies the type of key to generate, RSA is a widely used public key. 

`-b 4096` - This sets the key length to 4096 bits. 

`-C` - This allows you to add a comment to the key. 

When we enter this command, it will ask us to enter a file in which to save the key, this is where we want to name the key, I have named mine “**github_test”**. It then asks us if we want to enter passphrase, I have left this empty by pressing enter and confirming by pressing enter again. It will then confirm that a key pair has been generated for us. 

Example: 

![key_pair_generated.png](Images%2Fkey_pair_generated.png)

5) We can double check that the key pairs have been created by entering `ls` in the current `.ssh` directory we are in. It should show a private and a .pub keys. 

Example: 

![ls_keypairs.png](Images%2Fls_keypairs.png)

### Adding SSH key to GitHub account.

6) We can now add our public SSH key to our GitHub account, so we can commit and push our repository using SSH. On Git Bash we can print out our public key by entering `cat github_test.pub` . This will print out our public key, we can copy and paste this on your GitHub account. 

Example: 

![cat_sshkey.png](Images%2Fcat_sshkey.png)

We go into our **GitHub account > settings > SSH & GPG** 

![github_settings.png](Images%2Fgithub_settings.png)

**Add new SSH key** 

![ssh_key.png](Images%2Fssh_key.png)

And we finally copy and paste our public SSH key from Git Bash. The title can be the name of your SSH key. 

![ssh_key_github.png](Images%2Fssh_key_github.png)

It should now show that your SSH key has been generated and saved on GitHub. 

![key_saved.png](Images%2Fkey_saved.png)