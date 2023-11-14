---
Type:
  - Note
Status: In-Progress
tags:
  - git
---


| File/Directory           | Purpose                                                                                   |
|--------------------------|-------------------------------------------------------------------------------------------|
| `.gitignore`             | Specifies intentionally untracked files to be ignored.                                     |
| [[002 What is .gitattributes \| .gitattributes]]        | Configures how Git should handle certain files (line endings, binary/text file detection). |
| `.gitmodules`            | Defines submodules within a Git repository.                                                |
| `.gitkeep` or `.keep`    | A convention to ensure an otherwise empty directory is included in the repository.         |
| `.git`                   | Directory where Git stores its internal data and metadata for the repository.             |
| [[001 What is .gitconfig - Git config\|.gitconfig]]           | Global configuration file for Git, containing settings for the user's environment.        |
| `.gitignore_global`      | Global Gitignore file, applying rules across all repositories.                             |
| `.git/hooks/`            | Contains client or server-side scripts triggered at specific points in Git's execution.   |
| `.git/info/exclude`      | Similar to `.gitignore`, but specific to the repository and not shared.                     |
| `.git/logs/`             | Contains logs recording changes to the repository (commit history).                         |
| `.git/objects/`          | Stores all content for Git objects (blobs, trees, commits).                                 |
| `.git/refs/`             | Contains references or pointers to commits, branches, tags, etc.                             |
| `.git/HEAD`              | Points to the current branch or commit.                                                    |
| `.git/index`             | Staging area (index) where changes are prepared before committing.                          |

## Additional Notes

- The `.gitignore` and `.gitattributes` files are located in the root directory of the repository.
- The `.gitconfig` file is located in the user's home directory.
- The `.git`, `.gitmodules`, and `.gitkeep` files are located in the `.git` directory.

aditional to git especial files there are specificc vendors files that you can see here [[vendor files]]
