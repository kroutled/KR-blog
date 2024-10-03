### **Git Basics**

| Command                   | Description                                                       |
| ------------------------- | ----------------------------------------------------------------- |
| `git init`                | Initialize a new Git repository in your current directory.        |
| `git clone <repo-url>`    | Clone an existing repository from a URL.                          |
| `git status`              | Show the current state of the working directory and staging area. |
| `git add <file>`          | Stage a specific file for the next commit.                        |
| `git add .`               | Stage all changes in the current directory.                       |
| `git commit -m "message"` | Commit staged changes with a message.                             |
| `git log`                 | View the commit history.                                          |
| `git log --oneline`       | View the commit history in a compact format.                      |
| `git diff`                | Show changes between working directory and index/staging area.    |
| `git diff --staged`       | Show changes between staging area and last commit.                |

### **Branching & Merging**

| Command                         | Description                                                    |
| ------------------------------- | -------------------------------------------------------------- |
| `git branch`                    | List all branches.                                             |
| `git branch <branch-name>`      | Create a new branch.                                           |
| `git checkout <branch-name>`    | Switch to a different branch.                                  |
| `git checkout -b <branch-name>` | Create a new branch and switch to it.                          |
| `git merge <branch-name>`       | Merge a branch into the current branch.                        |
| `git branch -d <branch-name>`   | Delete a branch (only if fully merged).                        |
| `git branch -D <branch-name>`   | Force delete a branch.                                         |
| `git stash`                     | Save changes for later without committing.                     |
| `git stash pop`                 | Apply the most recent stash and remove it from the stash list. |
| `git stash list`                | View saved stashes.                                            |

### **Remote Repositories**

|Command|Description|
|---|---|
|`git remote -v`|View remote URLs linked to your repository.|
|`git remote add origin <url>`|Add a remote repository with the name `origin`.|
|`git push -u origin <branch-name>`|Push to a remote branch and set it as the upstream for future pushes.|
|`git push origin <branch-name>`|Push local changes to a remote repository.|
|`git push --all origin`|Push all branches to the remote repository.|
|`git pull`|Fetch and merge changes from the remote repository.|
|`git fetch`|Fetch changes from the remote repository (without merging).|

### **Undoing Changes**

| Command                     | Description                                                              |
| --------------------------- | ------------------------------------------------------------------------ |
| `git reset <file>`          | Unstage a file (leave changes in working directory).                     |
| `git reset --hard <commit>` | Reset the working directory and index to a previous commit (dangerous!). |
| `git checkout -- <file>`    | Discard changes in the working directory for a file.                     |
| `git revert <commit>`       | Create a new commit that undoes changes from a specific commit.          |
| `git reset HEAD~1`          | Undo the last commit, keep changes in the working directory.             |

### **Viewing and Comparing Changes**

|Command|Description|
|---|---|
|`git show <commit>`|Show the changes in a specific commit.|
|`git diff <branch-name>`|Show the differences between your working directory and a branch.|
|`git log --graph --oneline --all`|View the history of all branches in a compact graph.|

### **Tagging**

|Command|Description|
|---|---|
|`git tag`|List all tags in the repository.|
|`git tag <tag-name>`|Create a new tag at the current commit.|
|`git tag -a <tag-name> -m "message"`|Create an annotated tag with a message.|
|`git push origin <tag-name>`|Push a tag to the remote repository.|
|`git push --tags`|Push all tags to the remote repository.|

### **Configuration**

|Command|Description|
|---|---|
|`git config --list`|View all Git configuration settings.|
|`git config user.name "Your Name"`|Set your Git username.|
|`git config user.email "you@example.com"`|Set your Git email address.|
|`git config --global user.name "Your Name"`|Set your Git username globally for all repositories.|
|`git config --global core.editor "vim"`|Set the default text editor for Git globally.|

### **Working with Commits**

|Command|Description|
|---|---|
|`git commit --amend`|Amend the last commit (e.g., to fix the commit message).|
|`git cherry-pick <commit>`|Apply the changes from a specific commit on top of your current branch.|

### **Git Aliases (Optional, for Convenience)**

You can create aliases for frequently used commands:

```bash
git config --global alias.co checkout 
git config --global alias.br branch 
git config --global alias.cm commit 
git config --global alias.st status
```

### **Git Rebase**

|Command|Description|
|---|---|
|`git rebase <branch>`|Rebase the current branch on top of another branch.|
|`git rebase --continue`|Continue the rebase after resolving conflicts.|
|`git rebase --abort`|Abort the rebase process.|
