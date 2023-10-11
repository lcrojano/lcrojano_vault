# Syncing Obsidian with Different Devices

### 1. Install Obsidian Desktop
Make sure to install Obsidian on your desktop computer.
### 2. Install Obsidian Mobile
Likewise, install Obsidian on your mobile device.
### 3. Set Up Syncing
To keep your notes in sync between your desktop and mobile, you can use a tool like https://syncthing.net/. It simply copies your files from one device to another, without hosting them. This way, your notes are accessible on both devices.

**Additional Steps for Syncing:**

### a. Download and Install Syncthing
Visit the Synching website and download the application for your desktop. Follow the installation instructions provided.

### b. Configure Syncthing
After installing https://syncthing.net/, open the application and configure it to synchronize the folders containing your Obsidian notes on both your desktop and mobile devices. Ensure you set up a reliable sync schedule to keep your notes up to date.

---

# Syncing with Git and GitHub

## 1. Consider Obsidian Git
You can also use Obsidian Git to manage your notes. However, there might be limitations when using it on mobile due to a lack of a complete Git version.

**Additional Steps for Using Obsidian Git:**

### a. Install Git on Mobile (if possible)
Check if there's a mobile Git client available for your device. This will allow you to use Obsidian Git on your mobile.

### b. Sync with Desktop Git
When using Obsidian Git, ensure that you synchronize your notes with your desktop's Git repository. This keeps your mobile notes up to date with changes made on your desktop.

## 2. Challenges with Obsidian in WSL2
Working with Obsidian inside Windows Subsystem for Linux (WSL2) can be a bit complicated. You may encounter compatibility issues that need attention.

**Additional Considerations for WSL2:**

### a. System Compatibility
Make sure your system meets the requirements for running WSL2. Check the official documentation for any updates or prerequisites.

### b. Compatibility Mode
Try running Obsidian in compatibility mode if you encounter issues within WSL2. Some users find that this resolves compatibility problems.

---

# Troubleshooting SSH for Git in Obsidian

If you're having issues with using Git in Obsidian with SSH, here are some common problems:

**Additional Steps for SSH Troubleshooting:**

### a. Generate SSH Keys
[[Creating ssh key in windows.]]
If you haven't already, generate SSH keys on your local machine. Use `ssh-keygen` and follow the prompts. Ensure your SSH public key is added to your GitHub account.

### b. Test SSH Connection
Use the `ssh -T git@github.com` command to verify that your SSH connection to GitHub is functioning correctly.

### c. Check Permissions
Make sure your SSH keys have the correct permissions and that your SSH agent is running.

---

