as seen in [[Daybook|Daybook]]

- **Work Log:**
	- Solved large file management in git
	- Implemented [[Git Large File Storage| Git Large File System LFS ]]for files larger than 100m
    
- **Learning Notes:**
    - Topic: Git Large Files management
    - Resources:
	    - Git Large Files [[Git Large File Storage]]
        
- **Problem-Solving:**
    - Issue: Files larger than 50 to 100 mb emit a warning at git push to remote.
    - Steps Taken:
        Installed Git large file storage
    
    - Results:
        Upload all files to github without problem.
        
- **Project Management:**
    - Project:
    - Activities:
    - Decisions:
        
- **Communication Log:**
    - Meeting:
    - Attendees:
    - Discussions:
    - Action Items:
        
- **Code Snippet:**
    - Language: Git
    - Purpose: Install and push files larguer than 100mb
    - Code:
```
    git lfs track "*.pdf*"
```
        
    - Usage:

