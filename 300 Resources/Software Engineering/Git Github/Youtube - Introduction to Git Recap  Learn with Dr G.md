---
Type:
  - video
tags:
  - git
---

# [Introduction to Git Recap | Learn with Dr G](https://www.youtube.com/watch?v=9uGS1ak_FGg)

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/9uGS1ak_FGg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

  
### Git Recap from "Intro to Git" YouTube Video

1. **Setting Up User Information**: Configuring your username and email in Git using `git config` to let Git know who is making the commits.
    
2. **Initializing a Git Repository**: Creating a new folder (e.g., 'cats') and initializing it as a Git repository using `git init`.
    
3. **Creating and Tracking Files**:
    
    - Creating a new file (e.g., 'index.html') in the repository.
    - Checking the status with `git status` to see the untracked file.
    - Using `git add .` to start tracking changes in the repository.
    - Committing the changes with `git commit -m "commit message"` to save the version of the repository.
4. **Modifying Files**:
    
    - Making changes to the 'index.html' file (e.g., adding code).
    - Using `git add .` or `git add -A` to track changes made.
    - Committing the modified file with a descriptive message using `git commit -m "commit message"`.
5. **Working with .gitignore**:
    
    - Adding a `.gitignore` file to specify files or file types not to be tracked by Git.
    - Using `git add .` and `git commit -m "commit message"` to track and commit changes.
6. **Handling Typos or Small Changes**:
    
    - Fixing a quick typo in a committed file using `git commit --amend --no-edit`.
7. **Recovering Deleted Files**:
    
    - Recovering a file deleted by `rm` with `git checkout -- filename`.
    - Reverting Git's knowledge of file removal by `git reset HEAD filename`.
8. **Undoing Commits**:
    
    - Reverting to the previous commit state using `git reset --hard HEAD~1`.
    - Undoing specific changes made in a commit using `git revert --no-edit HEAD`.
9. **Navigating to Specific Commits**:
    
    - Checking out a specific commit using its hash to reset the repository to a previous state.

These steps cover a comprehensive journey from basic Git setup to handling file changes, recoveries, and reverting to specific commit states.