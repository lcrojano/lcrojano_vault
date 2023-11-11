---
url: https://docs.github.com/en/get-started/getting-started-with-git/configuring-git-to-handle-line-endings
Type:
  - Note
tags:
  - git
Status: Completed
---

These warnings indicate that Git is detecting a change in line endings (LF, which stands for Line Feed) in your files. It's notifying you that the line endings in some files are going to be replaced with CRLF (Carriage Return + Line Feed) the next time Git interacts with these files.

This warning often occurs when working on a project across different platforms (Windows, macOS, Linux), and Git is attempting to standardize line endings. Git uses LF by default on Unix-based systems and CRLF on Windows.

If you prefer to keep LF line endings in your files (common in Unix-based systems), you can configure Git to avoid converting them. You can use the following command:

`git config --global core.autocrlf input`

This command configures Git to convert CRLF line endings to LF on input but not the other way around.

If you're working in a cross-platform environment with collaborators using different line ending conventions, you might want to use a .[[gitattributes example]] file to specify how line endings should be handled for specific files or paths. This provides more fine-grained control over line ending handling in your repository.