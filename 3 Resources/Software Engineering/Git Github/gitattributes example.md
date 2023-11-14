Here's an example of a common `.gitattributes` file:

plaintextCopy code

``` bash
# Set the default behavior
* text=auto

# Denote binary files
*.png binary
*.jpg binary
*.gif binary
*.pdf binary

# Set specific handling for code files
*.js text
*.css text
*.html text
*.py text
*.java text

# Set specific handling for documentation files
*.md text
*.txt text

# Ignore generated files
/build/ -diff
/dist/ -diff
/node_modules/ -diff

# Specify end-of-line normalization for specific files or paths
# For example, force LF line endings in the "scripts" directory
scripts/* eol=lf
```

In this example:

- `* text=auto`: This sets the default behavior to automatically detect and normalize line endings.
    
- `*.png binary`, `*.jpg binary`, `*.gif binary`: These lines specify that certain file types (binary files like images) should be treated as binary and not have their line endings modified.
    
- `*.md text`, `*.sh text`, `*.html text`: These lines specify that files with certain extensions (Markdown, shell scripts, HTML) should have their line endings normalized.
    
- `scripts/* eol=lf`: This line specifies that files in the "scripts" directory should have LF line endings.
    

You can customize the `.gitattributes` file based on your project's needs, specifying how Git should treat different files or paths regarding line endings and binary/text status.

This example assumes:

- Text files are automatically detected and normalized.
- Common code file extensions are treated as text.
- Markdown and text files are treated as text.
- Binary files like images and PDFs are denoted as binary.
- Generated files and folders like `/build/`, `/dist/`, and `/node_modules/` are ignored in diffs.
- LF line endings are enforced in files under the "scripts" directory.

