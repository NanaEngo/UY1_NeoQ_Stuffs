# Git

> A guide to setting up Git

## Installation on Linux

[Git](https://git-scm.com/download/linux) - Git is a free and open source distributed version control system.

Detailed documentation is available at [Git-gittutorial DOcumentation](https://git-scm.com/docs/gittutorial)

### Installing Git

In terminal:
```
sudo apt install git-all
```

### Git Command Documentation

To get documentation for a command, say ```git log```:
```
man git-log
```
Or:
```
git help log
```

### Configuring Name and Email

To add ```user_name```:
```
git config --global user.name "user_name"
```

To add ```user_email```:
```
git config --global user.email "user_email"
```

### Initializing Git

To initialize any project in its directory:
```
git init
```

### Cloning a Repository

To clone a repository with url ```git_repo_url```:
```
git clone git_repo_url
```

### Adding Content

To add new content:
```
git add
```
To add all files in the entire working tree:
```
git add -A :/
```

### Commiting Changes

To commit changes with a message ```msg```:
```
git commit -m "msg"
```

To commit changes by adding all the new contents:
```
git commit -a
```

### Removing Commits

### Removing Cached .gitignore Files

### Adding Remote

To add a new remote ```origin``` with url ```remote_url```:
```
git remote add origin remote_url
```

To remove remote ```origin```:
```
git remote remove origin
```

To view details of remote ```origin```:
```
git remote show origin
```

To view all remotes associated with current directory:
```
git remote
```

### Pushing into Git Repository

To push local commits to master branch in the repository folder:
```
git push origin master
```

### Pulling from Git Repository

To pull changes from the Git Repository:
```
git pull origin master
```
