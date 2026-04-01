## Task 1

- To verify git is installed check with command git --version
- To setup your identity

```
git config --global user.name " "
git config --global user.email " "

```

- To verify config 

```
git config --list

```

## Task 2

1. mkdir devops-git-practice
2. To initialize git repo use 

```
git init
```
3. Display current stage of working directory and staging directory

```
git status
```
4. .git directory has 5 files and 5 directories

Files

- HEAD: A file that points to tip of current branch which indicates which branch is checked out
- config: This file has remote URL info , user info 
- index: This is staging area file , a snapshot of working tree use to prepare changes for next commit
- description: A file used by the GitWeb program to display a description of the repository

Folder

- objects: This is like DB of git stores all content of your project files as blobs , directores as tree  and commit informations
- refs: This folder stores pointers (references) to commit hashes, which are used to keep track of branches and tags.
    refs/heads: Contains files , one for each local branch that store hash on latest commit 
    refs/tags: Contains files for each tag , storing commit hash associated with specific version
    refs/remotes: Stores recently seen commit ID for remote tracking branches
- hooks: Contains sample scripts (hooks) that can be configured to run automatically at specific points in the Git workflow, such as before a commit (pre-commit) or after an update (post-update).
- logs/: This directory stores the history of all local commit activity (reflogs) for branches and other references, which helps in recovering lost commits or managing history.
- info/: Contains global exclusion patterns, similar to a personal .gitignore file, that are not shared with others in a collaborative project.

## TASK 3,4,5 refer to git-commands.md

## Task 6

1. git add will add files and changes done in staging directory and git commit will commit changes and create permanent snapshot in repository
2. Staging Area is a intermediate layer where it is decided which changes are needed to be commited and which are not. There is no direct commit because it give controls to do selective commits
3. git log shows commit id,author,date and commit message
4. .git folder is a hidden directory which has all commits and history stored and if we delete it then the directory will become normal folder and loses all version control history
5. Working directory means where files are edited ( Code development ) , Staging area means where changes are prepare before commiting and repository means where final commits changes are stored.
