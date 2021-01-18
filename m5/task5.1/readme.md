# Linux Essentials
## TASK 5.1
### Part 1

1. Installed Ubuntu 16.04 in VirtualBox. Logged in as root.

2. Changed the password for the root user using the command
`passwd root`</br>(see 5.1.1.1)</br>
![5.1.1.1](./images/5.1.1.1.jpg)</br>
This changed the system file /etc/shadow.

3. (see 5.1.1.2)</br>
![5.1.1.2](./images/5.1.1.2.jpg)</br>
As we can see from the screenshot, the system has pseudo-users. An important distinguishing feature is that they do not have an interpreter. And also their id > 1000.
For example, deamon is used for system services. On my system its uid = 1
There is also a root user. This is the user who owns all the files in current system.
By default, its uid = 0.
uid < 1000 is used for regular users.

4. To add or change user information we will use the `usermod` command
The `usermod` command with the "-c" parameter will allow us to add additional information about the user, such as last name first name,
phone number, rating in computer games.
(see 5.1.1.3)</br>
![5.1.1.3](./images/5.1.1.3.jpg)

5. By using `man passwd`, I found 2 interesting keys:</br>

  -e "Immediately expire an account's password. This in effect can force a user
to change his/her password at the user's next login."</br>
(see 5.1.1.4 and 5.1.1.5)</br>
![5.1.1.4](./images/5.1.1.4.jpg)</br>
![5.1.1.5](./images/5.1.1.5.jpg)</br>
 -x Set the maximum number of days a password remains valid. After MAX_DAYS, the password is required to be changed.</br>
(see 5.1.1.6)</br>
![5.1.1.6](./images/5.1.1.6.jpg)</br>
Let's do the same research for the usermod command</br>
 -e, --expiredate EXPIRE_DATE
    The date on which the user account will be disabled. The date is
    specified in the format YYYY-MM-DD.</br>
 -l, --login NEW_LOGIN
    The name of the user will be changed from LOGIN to NEW_LOGIN. Nothing
    else is changed. In particular, the user's home directory or mail spool should probably be renamed manually to reflect the new login name.</br>
    ```
    usermod -l zaza_02 zaza_01
    ```
    Changed the login, but did not change the home directory. The directory must be renamed manually. (see 5.1.1.7)
    ![5.1.1.7](./images/5.1.1.7.jpg)

6. More and less are very similar commands, but less is more convenient, there I can scroll the text in the opposite direction,
control with enter and space. To exit the viewer press q
to find something, I entered "/*some_text"</br>
Very helpful commands. Looked at .bashrc content using less command
(see 5.1.1.8)
![5.1.1.8](./images/5.1.1.8.jpg)

7. I installed finger. Than opened the manual, looked for information that will help me to complete the task.
Than created the .plan file in the user's home directory and wrote my plan there. (see 5.1.1.9)
![5.1.1.9](./images/5.1.1.9.jpg)

8. For this task, the -l parameter will suffice
(see 5.1.1.10)</br>
![5.1.1.10](./images/5.1.1.10.jpg)</br>
As we can see  letter "d" indicates that the file is a directory.

### Part 2

1. The `tree` command is able to display the structure of all directories on the system, in the form of a tree.
If we just enter the `tree` in home directory, we will see all the folders, subfolders and files in the form of a tree.
The `tree` has a huge number of options.</br>
First of all, the `-f` option which prefixes the path. Which can be useful for writing all sorts of scripts.
Also, we can add the `-d` option, only folders will be displayed.
We can also set a restriction on showing folders with more files than we want to see.</br>
For example `tree -d --filelimit 22` will display us only directories with no more than 22 files.</br>
By default, `tree` does not list hidden folders. To see them, we can use the `-a` option.</br>
The `-D` option will print files with the date they were last modified.</br>
The `-P` option allows us to search for files with the requested mask. In this case, the file name must be enclosed in quotation marks.</br>
The `--prune` option will exclude from the output all folders that do not contain the file we are looking for.</br>
For example `tree -P '*.py' --prune`
will show us only those directories that have '*.py' files and `--prune` will exclude from the output all folders that have no files
matching the output template. (see 5.1.1.11)</br>
![5.1.1.11](./images/5.1.1.11.jpg)</br>

The next command will print us all files named 'c' with all possible formats. `tree -P 'c.*' --prune` (see 5.1.1.12)</br>
![5.1.1.12](./images/5.1.1.12.jpg)</br>

To display all files containing 'c', I entered the next command:
`tree -P '*c*.*' --prune` (see 5.1.1.13)</br>
![5.1.1.13](./images/5.1.1.13.jpg)</br>

To list all directories and subdirectories up to and including the second level, used the command:
`tree -L 2` (see 5.1.1.14)</br>
![5.1.1.14](./images/5.1.1.14.jpg)</br>

2. The `file` can be used to determine the type of file.</br>
For example, I went to the /bin and
wrote the command `'file *` (see 5.1.1.15)</br>
![5.1.1.15](./images/5.1.1.15.jpg)</br>
Here we see symbolic links, scripts, binaries.

3. An absolute link contains the full path from the root directory to a file, for example, to go from the home directory to etc by an absolute path we write: `cd /etc` and we find ourselves in the etc directory, wherever we were before.</br>
Relative path is the path from the current directory. For example, the command that will allow us to get from the zaza directory to the zaza_01 directory will look like as follows: `cd ../zaza_01`
If we want to run a file that is in the current directory, we can do this using a relative link. (see 5.1.1.16)</br>
![5.1.1.16](./images/5.1.1.16.jpg)</br>
The `cd` command with no arguments will take us to our home directory wherever we are.

4. `ls` has a large number of possible parameters.
For example: `ls -i` will display the index number of each file. (see 5.1.1.17)</br>
![5.1.1.17](./images/5.1.1.17.jpg)</br>

Multiple parameters can be combined if needed. (see 5.1.1.18)</br>
![5.1.1.18](./images/5.1.1.18.jpg)</br>

When we use `ls -a` we see all files, even hidden ones.</br>
When we use `ls -l` we see all of our files as a list that contains additional information. Such as permissions, the owner of the file,
weight, time of the last file modification.







I will try to finish before the lecture 18/01/2021.
