# 🌱 Git & GitHub Basics: Your Project Time Machine ⏳

> **Git is like a super-powered "Save Game" system for your projects!**

It helps you:
- 📁 Save different versions of your work
- ↩️ Go back to previous versions if you make mistakes
- 👥 Collaborate with others without file conflicts
- ☁️ Store your projects online safely

---

## Table of Contents

1. [🛠️ Install Git](#-install-git)
2. [👤 Configure Git](#-configure-git)
3. [🚀 Initialize a Repository](#-initialize-a-repository)
4. [💾 Save Your Work](#-save-your-work)
5. [📥 Clone a Repository](#-clone-a-repository)
6. [☁️ Push to GitHub](#-push-to-github)
7. [🔄 Pull Latest Changes](#-pull-latest-changes)
8. [🔍 Git Cheat Sheet](#-git-cheat-sheet)
9. [🖱️ GitHub Desktop (GUI Option)](#-github-desktop-gui-option)
10. [🌈 Workflow Summary](#-workflow-summary)

---

## 🛠️ Install Git

### On Linux (Debian/Ubuntu)
```bash
sudo apt update
sudo apt install git-all
```

### On macOS
```bash
brew install git
```

### On Windows
Download from [git-scm.com](https://git-scm.com/download/win)

> 💻 **Note**: You only need to install Git once!

---

## 👤 Configure Git

Set your identity (required for commits):

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

> 📝 **Important**: Replace with your actual name and email!

### Verify configuration
```bash
git config --list
```

---

## 🚀 Initialize a Repository

1. Navigate to your project folder:
   ```bash
   cd ~/projects/my-awesome-project
   ```

2. Initialize Git:
   ```bash
   git init
   ```

> ✨ **What happens**: Creates a hidden `.git` folder that tracks all changes.

### Check status
```bash
git status
```

---

## 💾 Save Your Work

### Stage files (prepare for saving)
```bash
# Stage all changed files
git add .

# Stage specific file
git add filename.txt
```

> 📦 **Tip**: Use `git status` to see what's staged.

### Commit changes (save the snapshot)
```bash
git commit -m "Your descriptive message here"
```

> 💬 **Good commit messages**:
> - ✅ "Fixed login button color"
> - ✅ "Added user authentication"
> - ❌ "Stuff" (Too vague!)

---

## 📥 Clone a Repository

Download an existing project from GitHub:

```bash
git clone https://github.com/username/project-name.git
```

> 🌐 **Example**:
> ```bash
> git clone https://github.com/freeCodeCamp/freeCodeCamp.git
> ```

> 📁 **What happens**: Creates a new folder with the entire project.

---

## ☁️ Push to GitHub

### 1. Create a repository on GitHub
Go to [github.com/new](https://github.com/new) and create an empty repository.

### 2. Connect your local repo to GitHub
```bash
git remote add origin https://github.com/yourname/yourproject.git
```

### 3. Upload your work
```bash
git branch -M main
git push -u origin main
```

> 🚀 **First time**: You'll need to authenticate with GitHub credentials.

---

## 🔄 Pull Latest Changes

Get updates from the remote repository:

```bash
git pull origin main
```

> 🤝 **Use this**: When working with others or from multiple devices.
> 💡 **Tip**: Pull before you start working each day!

---

## 🔍 Git Cheat Sheet

| Command | Description | When to Use |
|---------|-------------|-------------|
| `git status` | Shows changed/staged files | Before committing |
| `git log` | Shows commit history | To see past versions |
| `git diff` | Shows line-by-line changes | Before committing |
| `git restore <file>` | Undo changes in a file | After mistakes |
| `git branch` | List all branches | To see branches |
| `git checkout -b <name>` | Create & switch to new branch | Starting new feature |
| `git merge <branch>` | Merge branches | Combining work |
| `git help` | Show help documentation | Anytime! |

---

## 🖱️ GitHub Desktop (GUI Option)

[![GitHub Desktop](https://desktop.github.com/images/desktop-icon.svg)](https://desktop.github.com/)

**Download**: [desktop.github.com](https://desktop.github.com/)

**Perfect for you if**:
- You're just starting out
- You prefer visual interfaces over commands
- You work mainly on your own projects

> ✅ Same Git power—no terminal needed!

---

### Installation

1. **Download**: Go to [desktop.github.com](https://desktop.github.com/)
2. **Install**: Run the installer for your OS (Windows/macOS/Linux)
3. **Sign in**: Use your GitHub account credentials

---

### Clone a Repository

1. Click **File** → **Clone Repository**
2. Choose from the list or paste a URL
3. Select local path and click **Clone**

> 📁 The repository will appear in your chosen folder.

---

### Make Changes & Commit

1. **Edit files** in your preferred editor
2. **Open GitHub Desktop** – changes appear automatically
3. **Write a summary** (required) and description (optional)
4. Click **Commit to main**

> 📝 **Tip**: Stage specific lines by highlighting them before committing.

---

### Push to GitHub

1. After committing, click **Push origin** at the top
2. Your changes are now on GitHub!

> ☁️ **Note**: Push regularly to backup your work.

---

### Create a New Repository

1. Click **File** → **New Repository**
2. Fill in:
   - **Name**: Your project name
   - **Description**: What it's about
   - **Path**: Where to save it
3. Check **Initialize with README** (recommended)
4. Click **Create Repository**

---

### Publish to GitHub

1. After creating locally, click **Publish repository**
2. Choose a name and visibility (Public/Private)
3. Click **Publish**

> 🔒 **Private**: Only you can see it. **Public**: Everyone can see.

---

### Pull Latest Changes

1. Click **Fetch origin** to check for updates
2. Click **Pull** to download changes

> 🔄 **Tip**: Pull before starting work each day!

---

### Create a Branch

1. Click **Current Branch** → **New Branch**
2. Name your branch (e.g., `feature/login-page`)
3. Click **Create Branch**

> 🌿 **Why branch?** Work on features without affecting main code.

---

### Merge a Branch

1. Switch to `main` branch
2. Click **Branch** → **Merge into current branch**
3. Select the branch to merge
4. Click **Merge**

---

### GitHub Desktop vs Command Line

| Action | GitHub Desktop | Command Line |
|--------|----------------|--------------|
| Clone | Click button | `git clone <url>` |
| Commit | Type & click | `git commit -m "msg"` |
| Push | Click button | `git push` |
| Pull | Click button | `git pull` |
| Branch | Click menu | `git checkout -b <name>` |
| Merge | Click menu | `git merge <branch>` |

---

### Keyboard Shortcuts

| Action | Windows | macOS |
|--------|---------|-------|
| Commit | `Ctrl+Enter` | `Cmd+Enter` |
| Push/Pull | `Ctrl+T` | `Cmd+T` |
| Search | `Ctrl+F` | `Cmd+F` |

---

### Troubleshooting

| Issue | Solution |
|-------|----------|
| **Can't sign in** | Check internet, verify credentials |
| **Changes not showing** | Refresh: View → Reload |
| **Push failed** | Pull first, resolve conflicts |
| **Wrong account** | File → Options → Accounts |

---

> 💡 **Pro Tip**: Use GitHub Desktop for daily work, learn command line for advanced features!

---

## 🌈 Workflow Summary

### Daily workflow
```mermaid
graph LR
    A[Edit Files] --> B[git add .]
    B --> C[git commit -m "message"]
    C --> D[git push]
    D --> E[Done!]
    E -.-> A
```

### Quick reference
1. `git add .` → Stage changes
2. `git commit -m "Message"` → Save snapshot
3. `git push origin main` → Upload to cloud
4. `git pull origin main` → Get updates

---

## 🎉 Congratulations! You've Got Git Superpowers! 💪

**Next Steps**:
- 🚀 Create your first GitHub repository
- 📝 Commit small changes daily
- 🐛 Explore GitHub Issues for project tracking
- 🔀 Learn about branches for feature development

> 💬 **Remember**: Every expert was once a beginner. Happy coding! 🚀

---

*UY1 Néo Quanticiens – Python Tricks Collection*
