# DevOps Introduction
## TASK 1.1

Installed and configured GIT on my workstation.
![Screenshot_1](./screenshots/1.jpg)

Cloned repo.
![Screenshot_2](./screenshots/2_clone.jpg)

Then I followed by the instruction step by step.
1. Created empty file readme.txt. Committed. ```git add .; git commit```
2. Created develop branch and checkout on it. ```git checkout -b develop```
3. Created index.html. Committed. ```touch index.html; git add .; git commit -m 'comment'```
4. Created images branch and checkout on it. Added images folder with cats.
Committed. ```git checkout -b images```
5. etc


Did all stuff until merging "images" and "styles" into "develop"
While trying to merge "styles" into "develop" conflict occurred.
Make sure that index.html from one branch doesn't conflict with another.
We can delete "separators" manually. Then commits. Conflict was resolved.

Used ```git log --oneline``` <br/>
![Screenshot_3](./screenshots/one_line.jpg)

For more detailed log we can use ```git log -p``` <br/>

![Screenshot_4](./screenshots/git_log-p.jpg)

Pushed all changes ```git push origin --all```

Save content from ```git reflog``` out of repo. <br/>
```git reflog > /c/Users/eaglevn/Desktop/my_epam_education_Win/task1.1_GIT.txt```<br/>
![Screenshot_5](./screenshots/git_reflog_out.jpg)

Added task1.1_GIT.txt to my repo. Pushed it.

*DevOps is a set of methodologies that help to synchronize and coordinate workflow across all areas of development. From planning to release.*
