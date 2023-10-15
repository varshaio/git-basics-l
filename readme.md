# Git Commands

[git init](#git-init)

[git add](#git-add)

[git commit](#git-commit)

[git log](#git-log)

[git checkout](#git-checkout)

[git branch](#git-branch)

[Alternative way of creating a branch](#alternative-way-of-creating-a-branch)

[git merge](#git-merge)

[What is the "HEAD"?](#what-is-the-head)

[What is "detached HEAD"?](#what-is-detached-head)

## git init

To initialize a repository

## git add

To add new or untracked and modified files from working directory to the staged area.

Stage are is also known as index, technically.

## git commit

To commit the new files or modified files from index to the repository or the object area.

Techinically, both stage and objects are are part of the repository.

## git log

To see the details of all commits.

A commit log consists of the commit hash, author with email, commit date, message.

## git checkout

To load or go to a specific commit.

To go to a specific branch.

Main purpose of checkout command is to move between different branches.

## git branch

To list all branches in the repository or to create a new branch.

Current working branch is often indicated with \* (asterisk).

A new branch is a replica of the branch from which it was created, it include history of all commits also. So, the new branch is identical to the parent branch.

Remember, untracked files are always present in the working directory irrespective of the branch currently active. On the other hand tracked files, the files already in the staging area, might be added or removed from the working directory depending on the status of a branch's staging area.

Also remember that, in normal circumtances, once we add a file in the staging area, it is always present in the staging area. That means commited files are also in the staging area, they are not removed from the staging area after being commited to the repository.

### Alternative way of creating a branch

Normally, we issue <code>git branch new_branch_name</code> command to create a branch and then to move the that branch we issue <code>git checkout newly_created_branch_name</code> command. So, it a two step process to move to a newly created branch and work with it.

But, there is a way to create a branch and move to it simultaneously.

We issue <code>git checkout -b new_branch_name</code> command.

## git merge

To merge another branch to this branch.

## What is the "HEAD"?

In a specific branch the latest is referred by a pointer called HEAD.

## What is "detached HEAD"?

When we checkout a specific commit in a branch, git does not know whether the commit belongs to this branch only or the parent branch. In such cases, if the commit belongs to both this and the parent branch, then the commit is known as the detached HEAD.

detached HEAD simply means the commit is not a part of a specific branch. A detached HEAD is itself treated as a branch. This means that we are now working with a specific commit, not with a specific branch.
