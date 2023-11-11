---
Type:
  - Note
Status: Completed
---
you can update configuration settings using the <mark style="background: #ADCCFFA6;">`git config`</mark> command. Here are the basic commands for updating different levels of configuration

**Updating Global Configuration:**
``` bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

**Updating Local Repository Configuration:** This sets configuration values only for the specific repository.
``` bash 
cd /path/to/your/repository 
git config user.name "Your Name" 
git config user.email "your.email@example.com"
```

**Updating System-Wide Configuration:** Use the `--system` flag to set configuration values system-wide, applying to all users on the machine.

``` bash
git config --system core.editor "vim"
```


**Updating Configuration File Directly:** 
You can also edit the Git configuration files directly. The global configuration file is usually located at `~/.gitconfig`.

 ``` bash 
nano ~/.gitconfig
    ```     

Remember to replace the placeholder values with your actual information. If you're unsure about the current configuration, you can use `git config --list` to view all configurations.

Be cautious when directly editing configuration files, and prefer using `git config` commands for safety and convenience.

**Other Useful configs:**
- [[Change the default branch name from master to main globally in Git]]
- [[Change Master to main on existing repository]]