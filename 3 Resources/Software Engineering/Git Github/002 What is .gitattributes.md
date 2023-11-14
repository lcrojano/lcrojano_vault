---
Type:
  - Note
Status: In-Progress
url: https://git-scm.com/docs/gitattributes
tags:
  - git
---

`.gitattributes` is a configuration file in Git that allows you to specify attributes for files in your repository. These attributes control how Git treats line endings, merges binary files, and more. Here's when to use it, when not to use it, and considerations for choosing guidelines:

### When to Use `.gitattributes`:

1. **Line Ending Normalization:**
    
    - Use it when working in a cross-platform environment (Windows, macOS, Linux) to ensure consistent line endings.
    - Specify `text=auto` to automatically normalize line endings based on the platform.
2. **Binary vs. Text Files:**
    
    - Use it to specify whether files are binary or text. This can be crucial for proper handling of files during merges.
    - For example, specify `*.png binary` to denote that PNG files are binary.
3. **Custom Rules for Specific Paths:**
    
    - Use it when you need to apply specific rules to files or paths in your project.
    - For instance, enforce LF line endings in a specific directory with `directory/* eol=lf`.

### When Not to Use `.gitattributes`:

1. **Small Projects:**
    
    - For very small projects where cross-platform collaboration and specific handling of files are not critical, you might not need `.gitattributes`.
2. **Single-Platform Development:**
    
    - If you are working in an environment where everyone uses the same platform and text file handling is not a concern, you might not need `.gitattributes`.