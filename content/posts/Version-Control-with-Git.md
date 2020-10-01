---
title: Version Control with Git
date: 2020-02-16T20:42:34-04:00
tags: [git]
categories: [tech doc]
draft: false
---

Study note of the Course: [Udacity Course: Version Control with Git](https://www.udacity.com/course/version-control-with-git--ud123)

## What is version Control
Example: Control -Z

Types of Version Control: Centralized and Distributed(e.g. Git)

Terminology: SCM(Source Control Manager)/VCS(Version Control System)

Git Setup and Config
```bash
# sets up Git with your name
git config --global user.name "<Your-Full-Name>"
# sets up Git with your email
git config --global user.email "<your-email-address>"
# makes sure that Git output is colored
git config --global color.ui auto
# displays the original state in a conflict
git config --global merge.conflictstyle diff3
git config --list
git config --global core.editor "mvim -f"
```
<!--more-->

## Create A Repo
Method1: Create a new directory and “git init” in the dir.

Method2: “git clone …”

## Review A Repo’s History
```bash
git status
git log
# Info it displays include SHA, Author, Date, commit message …
```

Flags:

–oneline: Only SHA and commit messages are displayed

–stat: statistics of file changes

-p: patch: details of file changes

[PS] How to scroll down/up Command Line Pager?

shortcuts:

down:

- j: one line
- d: half page
- f: one page
up:

- k: one line
- u: half page
- b: one page

## Add Commits To A Repo
Three areas of Git system:

- Working directory
- Staging Index
- Repository directory
```bash
# From working dir to staging area
git add index.html
git add .
git diff # similar to git log -p
# From staging area to Repo dir
git commit  # core.editor will be opened
git commit -m "message"
```

How to ignore a file?

Create a file named “.gitignore” in the same path with “.git”

### About Globing?

-\*: Any number of characters including none
- \?: Any single character
- [abc]:
- [0-9]:
- [!C]: Except 'C'
- [!3-7]: Except [3-7]

## Tagging, Branching, and Merging
### Tagging
git tag -a v1.0 <SHA>
### Branching
```bash
# List branches
git branch
# Create a branch named sidebar
git branch sidebar
# Switch branches
git checkout sidebar
# Start position
git branch alt-sidebar <SHA>
# Delete a branch --delete or -d
git branch -d sidebar
# Shortcut for --delete --force
git branch -D sidebar
```
### Merging
`git merge [<branch>]  # merge the branch into current branch`

How to solve merge conflicts?
1. Decide not to merge. git merge --abort can be used for this.
2. Resolve the conflicts. Git will mark the conflicts in the working tree. Edit the files into shape and git add them to the index. Use git commit or git merge --continue to seal the deal. 

The area where a pair of conflicting changes happened is marked with markers <<<<<<<, =======, and >>>>>>>. The part before the ======= is typically your side, and the part afterwards is typically their side.  ||||||| marker is followed by the original text.

## Undoing Changes
```bash
# Update last commit message；reword: working dir 做了改动之后想与上次提交的commit合并
git commit --amend
git revert  # Create a new commit that undo a specific commit
git reset  # Be careful!
# Before resetting, you can create a backup branch on the most-recent commit
git branch backup

# restore file to status before modified(deleted)
git checkout -- filename
git checkout -- .
# delete newly created files(untracked)
git clean -i -d # Becareful! -i:interactive
```
### Relative Commit  References
- HEAD^, HEAD^^, HEAD^^^, HEAD^^2
- HEAD~, HEAD~2, HEAD~3

With a merge commit, ^ indicate the first parent; ^2  indicate the second parent. The first pare was the branch you were on when you ran git merge

### Git Reset's Flags

- --mixed  # Move the changes to working dir
- --soft # Move the changes to Staging Index
- --hard #Move the changes to trash

## References:
[Git Doc](https://git-scm.com/docs)
[Udacity Course: Version Control with Git](https://www.udacity.com/course/version-control-with-git--ud123)
Create a repo to track your computer's settings - https://dotfiles.github.io/
Try tackling some Git challenges with the [Git-it app](https://github.com/jlord/git-it-electron)


