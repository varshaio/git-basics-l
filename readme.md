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

[git switch](#git-switch)

[git ls-files](#git-ls-files)

[Deleting working directory files which are already staged](#deleting-working-directory-files-which-are-already-staged)

[git rm](#git-rm)

[How to undo unstaged changes?](#how-to-undo-unstaged-changes)

[git restore](#git-restore)

[Deleting untracked files and directories](#deleting-untracked-files-and-directories)

[git clean](#git-clean)

[How to undo staged changes?](#how-to-undo-staged-changes)

[git reset](#git-reset)

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

## git switch

From git 2.23 onwards.

To create new braches <code>git switch -c new_branch_name</code> and move between branches <code>git switch branch_name</code>.

With <code>git checkout</code>, we can work with both commits and branches, but <code>git switch</code> is specific to working with branches. Hence <code>git switch</code> has a clearly defined function.

## git ls-files

To see all files of a branch that are in the staging area.

## Deleting working directory files which are already staged

One way to delete a staged file from the working directory is to first delete the file from the working area the issue <code>git add file_name</code> command so that the changes for deletion are recorded to the staging area, then issue <code>git commit file_name</code> command to finally remove the file from the repository also.

another way is to use
<code>git rm file_name</code> <a id="git-rm"></a> command to remove the file directly from the staging area, then issue <code>git commit file_name</code> command to make changes in the repository also.

Idea behind this mechanism is that the files we see in our working directory are of two kinds only, first type of files is untracked files i.e. new files and second type of files is tracked files i.e. files that are in the staging area and modified files according to git. If we remove a file from the staging area then to conform to the working mechanism of git, that file will also be removed from the working directory automatically. All we have remaining to do is to commit the deletion change to the repository to make the change permanent.

## How to undo unstaged changes?
To undo the changes made to a staged file, issue <code>git checkout file_name_having_unstaged_changes</code>.

It will tell git to checkout the latest commit of the specified file, it will essentially remove any unstaged changes in the file.

To undo changes from all file or multiple file that are staged, issue <code>git checkout .</code> or <code>git checkout file_1 file_2</code> respectively.

**From git 2.23**

<code>git restore file_name</code> <a id="git-restore"><a> can be used.

## Deleting untracked files and directories
<code>git clean -dn</code> <a id="git-clean"></a> command lists the untracked files to be deleted.

<code>git clean -df</code> command delete untracked files forcefully.

## How to undo staged changes?

Traditional way:

<code>git reset file_name</code> <a id="git-reset"></a> to overwrite the staged version of the file with the latest commit version of the file.

<code>git checkout file_name</code> to overwrite the file in the working directory with the file in the staged area.

Remember, <code>git checkout</code> compares the contents of the file in current directory or working directory with the content of the file in the staged area. If there is no difference then no overwrite action will take place, else the file in the working directory will be replaced with the version of the file in the staged area.

From git 2.23

<code>git restore --staged file_name</code>

<code>git checkout file_name</code>

