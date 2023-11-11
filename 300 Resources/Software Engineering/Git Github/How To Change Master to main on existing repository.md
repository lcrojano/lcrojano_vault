---
Type:
  - Note
Status: Completed
tags:
  - git
---
If you have existing repositories, you may want to rename the existing "master" branch to "main." Here are the commands for that:

``` bash
# Rename the local branch 
git branch -m master main  
# Update the remote repository to use the new branch name 
git push -u origin main  
# Set "main" as the default branch for your local repository \

git symbolic-ref refs/remotes/origin/HEAD refs/remotes/origin/main
# Change the default branch locally git remote set-head origin -a
```

why use [[git symbolic-ref]]?