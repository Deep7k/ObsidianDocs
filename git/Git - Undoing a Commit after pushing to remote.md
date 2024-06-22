---
Author: Deepak N A
Date: 2024-06-23
---
## Introduction

One time while drunk I ran `cherry-pick` to merge changes from **dev** branch to **master** branch. it resulted in git conflict which my drunken brain pushed to GitHub which resulted in unwanted consequences. this guide will show show how to solve this but most importantly **Don't  push your changes to remote while drunk**
## Prerequisites

Before proceeding, ensure you have the following:

- Git installed on your local machine.
- Access to the GitHub repository where the commit was pushed.
- Basic knowledge of using Git commands.
## Steps

### 1. Identify the Commit to Undo

First, determine the commit you want to undo. You can find this by checking the commit history either on GitHub or using the `git log` command locally. you can use  [Git - Commands](Git%20-%20Commands.md) for useful git commands

In my case I wanted to undo the commit `32263d5 Added function Send-keystrokes`
### 2. Undo the Commit Locally

#### Fetch Updates

Ensure your local repository is up to date with the remote (GitHub) repository:

```bash
git fetch origin
git checkout master
git pull origin master
```
#### Revert the Commit

Use `git revert` to create a new commit that undoes the changes introduced by the cherry-picked commit:

```bash
git revert <commit-hash>
```

Replace `<commit-hash>` with the actual hash of the commit you want to undo. This command will open your default editor to add a revert commit message. Save and close the editor when done. In my case I ran

```example
git revert 32263d5
```
### 3. Push the Revert Commit to GitHub

After successfully reverting the commit locally, push the changes to the GitHub repository:

```bash
git push origin master
```
### 4. Verify on GitHub

Go to your GitHub repository and navigate to the `master` branch. You should see the new revert commit listed in the commit history.

**Important Note**

- When you use `git revert`, it creates a new commit that undoes the changes introduced by the specified commit. This approach does not remove the commit from history but rather adds a new commit that effectively reverses the changes.
- This method is preferred in collaborative environments because it maintains a clear history and avoids disrupting other contributors who may have already pulled the changes.
## Conclusion

You have successfully undone a commit after pushing it to GitHub using `git revert`. 

This method preserves commit history and is useful for safely undoing changes without rewriting history. 
## References 

- [Git Documentation: git revert](https://git-scm.com/docs/git-revert)
