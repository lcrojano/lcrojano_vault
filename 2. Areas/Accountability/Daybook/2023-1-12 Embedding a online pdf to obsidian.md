as seen in [[🗃️ Daybook|🗃️ Daybook]]

- **Work Log:**
	- Created a GitHub repository to store all books and binary files that will be used as reference for obsidian
	- Implemented [[Git Large File Storage| Git Large File System LFS ]]for files larger than 100m
    
- **Learning Notes:**
    - Topic: Obsidian online pdf inside viewer
    - Resources:
	    - Repository [lcrojano/books (github.com)](https://github.com/lcrojano/books)
	    - Plugin [elias-sundqvist/obsidian-annotator: A plugin for reading and annotating PDFs and EPUBs in obsidian. (github.com)](https://github.com/elias-sundqvist/obsidian-annotator)
        
- **Problem-Solving:**
    - Issue: storing binary files in inside the vault, although is a good option is not best
    - User wanted to use annotation over pdfs provided  by obsidian an annotator plugin
    - we can improve by storing binary files outside vault
    - Steps Taken:
        Installed Git large file storage
        created a repository in GitHub which contains all pdf
        linked resulting pdf URLs using plugin annotator
        
    
    - Results:
        File rendered as expected.
        Files not stored in vault, resulting in low size vault.
        
- **Project Management:**
    - Project: [[Build a PARA - GTD framework]]
    - Activities:
    - Decisions:
        
- **Communication Log:**
    - Meeting:
    - Attendees:
    - Discussions:
    - Action Items:
        
- **Code Snippet:**
    - Language: Annotator plugin
    - Purpose: add a view to external pdf
    - Code:
```
    ---
	annotation-target: https://arxiv.org/pdf/2104.13478.pdf
    ---
```
        
    - Usage:
	    - put the code as an attribute of the page.

