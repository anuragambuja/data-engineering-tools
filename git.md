## Overview

#### Git originates from the Linux kernel development and was founded in 2005 by Linus Torvalds. The core of Git was originally written in the programming language _C, but Git has also been re-implemented in other languages, e.g., Java, Ruby and Python. 

#### A file in the working tree of a Git repository can have different states. These states are the following: 
  - untracked: the file is not tracked by the Git repository. This means that the file never staged nor committed. 
  - tracked: committed and not staged 
  - staged: staged to be included in the next commit 
  - dirty / modified: the file has changed but the change is not staged 

#### After modifying your working tree you need to perform the following two steps to persist these changes in your local repository: 
  - add the selected changes to the staging area (also known as index) via the `git add` command 
  - commit the staged changes into the Git repository via the `git commit` command 

#### The `git add` command stores a snapshot of the specified files in the staging area. It allows you to incrementally modify files, stage them, modify and stage them again until you are satisfied with your changes. 

#### After adding the selected files to the staging area, you can commit these files to add them permanently to the Git repository. _ Committing_ creates a new persistent snapshot (commit object) of the staging area in the Git repository. A commit object, like all objects in Git, is immutable. For committing the staged changes you use the `git commit` command. The commit object points to the individual files in this commit via a tree object. The files are stored in the Git repository as blob objects and might be packed by Git for better performance and more compact storage. Blobs are addressed via their SHA-1 hash. 

#### Users with sufficient authorization can send new version in their local repository to to remote repositories via the `push` operation. They can also integrate changes from other repositories into their local repository via the `fetch` and `pull` operation. 

#### HEAD is a symbolic reference most often pointing to the currently checked out branch. Sometimes the HEAD points directly to a commit object, this is called detached HEAD mode. In that state creation of a commit will not move any branch. If you switch branches, the HEAD pointer points to the branch pointer which in turn points to a commit. If you checkout a specific commit, the HEAD points to this commit directly. 


## Commands
- Initialize Git repository(/.git/): `git init`
- Check repository status: `git status`
- remembers all the changes we've committed so far, in the order we committed: `git log`
- The double dot operator allows you to select all commits which are reachable from a commit c2 but not from commit c1. The syntax for this is "c1..c2". A commit A is reachable from another commit B if A is a direct or indirect parent of B. List all commits which are in the `testing` but not in the `master` branch: `git log master..testing`. The triple dot operator allows to select all commits which are reachable either from commit c1 or commit c2 but not from both of them. This is useful to show all commits in two branches which have not yet been combined: `git log <branch1>...<branch2>`
- Show all local and remote branches that (local) git knows about: `git branch -a`
- Delete a branch (add --force (-f) option if something that hasn't been merged or use -D which combines -d -f together): `git branch -d <branch name>`
- To checkout and create a branch, use `git checkout -b new_branch`. This is same as doing: `git branch new_branch` and `git checkout new_branch`
- Files can be changed back to how they were at the last commit by using the command: `git checkout -- <target>`
- Remove the actual files from disk and stage the removal of the files: `git rm filename`
- Add changes to staging area to track the changes: `git add filename`
- Sometimes when you go to pull you may have changes you don't want to commit just yet. Use the command `git stash` to stash your changes, and `git stash apply` to re-apply your changes after your pull. 
- To store our staged changes: `git commit -m "Just added the file"`
- Unstage files: `git reset filename`
- Undo changes made in the working directory and staging area: `git reset --mixed`
- Check for changes in GitHub repository and pull down any new changes: `git pull origin master` `(= git fetch + git merge origin/ master)`
- Check what is different from our last commit: `git diff`. Add `--staged` option to see the changes you just staged 
- To update the local list of remote branches: `git remote update origin [--prune]`
- To push our local repo to the GitHub server: `git remote add`
- push our local changes to our origin repo. The -u tells Git to remember the parameters, so that next time we can simply run `git push`: `git push -u origin master`
- Merge your changes from the `other_branch` into the master branch (already into master branch): `git merge other_branch`
- Revert changes of commit: `git revert <commit id>`



