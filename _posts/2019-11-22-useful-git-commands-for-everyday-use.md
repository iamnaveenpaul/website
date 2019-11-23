---
title: Useful git commands for everyday use!
image: "/assets/default-social-image.png"
categories: git-commands
---

Lemme tell my experience. To execute certain actions with git, I’ve Googled a lot and came to this conclusion that it isn’t effective, rather it actually slowed me down a lot. I’ve noticed that the questions about git get the most views on [StackOverflow](https://stackoverflow.com/tags/git). There are some actions that we use a lot in git, so it’s a good thing to learn them, you have to discover it yourselves but I am going to help you a li’l bit in this regard where I learned from the internet, my friends and colleagues. Hope you find this tutorial useful.

Before I begin, please check the `git --version` on your machine, I use `2.12.2` in macOS, so it is recommended that you have this version or higher. [Here](https://git-scm.com/) is the official documentation of git where you can read the details about git commands, parameters and new versions.

**Table of Contents**

* Useful commands
* Git alias
* GUI clients
* Check before you commit
* Where to go from here

**Useful commands**

🔍 Status

Checking the status of staging area and working directory:

`git status`

Shows the changes between working directory and HEAD:

`git diff`

Shows all commits in a line:

`git log --oneline`

Shows commits that can be used for certain string to add or remove:

`git log -S 'LoginViewController'`

Search commits which contains a log message:

`git log — all — grep=’day of week’`

🔍 Tag

List all the tags:

`git tag`

Commit a tag:

`git tag -a 1.4 -m "my version 1.4"`

Remove remote tags:

`git push --delete origin tagname`

`git push origin :tagname`

Push a tag to remote:

`git push origin tagname`

Rename a tag:

```
git tag new old

git tag -d old

git push origin :refs/tags/old

git push --tags
```

Move a tag from one commit to another:

```
git push origin :refs/tags/<tagname>

git tag -fa tagname

git push origin master --tags
```

🔍 Remote

List all remote:

`git remote`

Rename a remote:

`git remote rename old new`

Remove tracking branches of a stale remote:

`git remote prune origin`

🔍 Branch

List all the branches:

`git branch`

Create and switch the branch on your local machine:

`git checkout -b branch_name`

Create the branch from commit:

`git branch branch_name sha1_of_commit`

Push the branch to remote:

`git push origin branch_name`

Rename other branch:

`git branch -m old new`

Rename the current branch:

`git branch -m new`

Rename the remote branch:

```
git branch -m old new               # Rename branch locally   

git push origin :old                 # Delete the old branch   

git push --set-upstream origin new   # Push the new branch, set local branch to track the new remote
```

Delete a branch:

```
git branch -D the_local_branch

git push origin :the_remote_branch
```

Delete all but master local branches

`git branch | grep -v "master" | xargs git branch -D`

🔍 Commit

Undo last commit:

`git reset --hard HEAD~1`

Squeeze last n commits into one:

```
git rebase -i HEAD~5

git reset --soft HEAD~5

git add .

git commit -m "Update"

git push -f origin master
```

Move last commits into a new branch:

```
git branch newbranch

git reset --hard HEAD~3 # Go back 3 commits. You *will* lose uncommitted work.*1

git checkout newbranch
```

🔍 Cherry Pick

Add some commits to the top of the current branch:

`git cherry-pick hash_commit_A hash_commit_B`

🔍 Reflog

Show reflog:

`git reflog`

Get commit:

```
git reset --hard 0254ea7

git cherry-pick 12944d8
```

🔍 Revert

Revert the previous commit:

```
git revert HEAD

git commit
```

Revert the changes without making commit  from previous 3 commits:

`git revert --no-commit HEAD~3..`

🔍 Amend

Amend previous commit:

```
git commit --amend

git commit --amend --no-edit

git commit --amend -m "New commit message"
```

[This](http://stackoverflow.com/questions/8981194/changing-git-commit-message-after-push-given-that-no-one-pulled-from-remote) is changing git commit message after push:

```
git commit --amend -m "New commit message"

git push --force <repository> <branch>
```

🔍 Checkout

Checkout a tag:

```
git checkout tagname

git checkout -b newbranchname tagname
```

Checkout a branch:

`git checkout destination_branch`

Using -m if there is a merge conflict:

`git checkout -m master // from feature branch to master`

Checkout a commit:

```
git checkout commit_hash

git checkout -b newbranchname HEAD~4

git checkout -b newbranchname commit_hash

git checkout commit_hash file
```

Checkout a file:

`git checkout c5f567 -- Relative/Path/To/File`

🔍 Stash

Save changes to stash:

```
git stash save "stash name"

git stash
```

List all the stashes:

`git stash list`

Apply a stash:

```
git stash pop

git stash apply

git stash apply stash@{2}
```

🔍 Rebase

Rebase the current branch to master:

`git rebase master // rebase the current branch onto master`

Continuing rebase:

`git rebase --continue`

Abort rebase:

`git rebase --abort`

🔍 .gitignore

Remove files that just have been declared in .gitignore:

```
git rm -r --cached .

git add .

git commit -am "Remove ignored files"
```

🔍 Index

Remove the untracked files:

`git clean`

Remove the file from index:

`git reset file`

Reset index for matching the most recent commit:

`git reset`

Reset index and also the working directory for matching the most recent commit:

`git reset --hard`

🔍 Misc

Get the changes during a git rebase:

```
git checkout --ours foo/bar.java

git add foo/bar.java
```

Get the changes during a git merge:

```
git pull -X theirs

git checkout --theirs path/to/the/conflicted_file.php

git checkout --theirs .

git add .

git checkout branchA

git merge -X theirs branchB
```

Merge commits from the master into the feature branch:

```
git checkout feature1

git merge --no-ff master
```

Find any bug in commit history with a binary search tree style:

```
git bisect start

git bisect good

git bisect bad
```

**Git alias**

Consider using git alias if there are commands which you use a lot. You can just type `git st` for making alias for `git status`:

`git config — global alias.st status`

You can learn some aliases from [thoughtbot](https://github.com/thoughtbot/dotfiles/blob/master/gitconfig) and [mathiasbynens](https://github.com/mathiasbynens/dotfiles/blob/master/.gitconfig). The configurations here are stored in `.gitconfig` file.

**GUI clients**

It’s cool and faster for doing things in command line. To view branches and commits however it’s more comfortable and visualizing to use a GUI client. There are list of all GUI clients [here](https://git-scm.com/download/gui/mac), I basically use [SourceTree](https://www.sourcetreeapp.com/).

Check before you commit

I usually mark my experiment with `// <TEST>` because we don’t want the experiment code to step into our commit, but it sometimes forgets to unstage that.

Git has improvement on its commit hook for using hookspath makes itself globally, with 2.9 onwards.

First, we need to create a file `pre-commit`, and place it into, say as an example, `/Users/khoa/hooks`:

Then, run `git config core.hooksPath /Users/khoa/hooks` in your project.

Git won’t let you commit, when you want to commit with that pattern. Check the following once, to make this work in SourceTree: SourceTree and pre commit hook

**Where to go from here**

This is just a top pile of a big heap on what git can do but if you want to learn more, check out the following links.

* [Atlassian Git Tutorial](https://www.atlassian.com/git/tutorials/setting-up-a-repository): overview of how to set up a repository (repo) under Git version control
* [git-cheat-sheet](https://github.com/arslanbilal/git-cheat-sheet): Git cheat sheet saves you from learning all the commands by heart. 
* [Learn Enough Git to Be Dangerous](http://www.learnenough.com/git-tutorial) 
* [Git Workflows for Pros: A Good Git Guide](http://www.toptal.com/git/git-workflows-for-pros-a-good-git-guide)
* [Git from the inside out](https://codewords.recurse.com/issues/two/git-from-the-inside-out): The essay focuses on the graph structure that underpins Git 
* [git-game](https://github.com/git-game/git-game): terminal game to test git skills
* [Introduction to Git](https://www.youtube.com/watch?v=xbLVvrb2-fY) — talk by Scott Chacon 
* [Git Tutorial — Git Fu With The Command Line](http://www.raywenderlich.com/74258/git-tutorial-intermediate)
* [Git Immersion](http://gitimmersion.com/): The surest path to mastering Git is to immerse oneself in its utilities and operations, to experience it first-hand 
* [git-flight-rules](https://github.com/k88hudson/git-flight-rules): Flight rules for git
* [gitflow](https://github.com/nvie/gitflow): Git extensions to provide high-level repository operations for Vincent Driessen’s branching model
* [diff-so-fancy](https://github.com/so-fancy/diff-so-fancy): Good-lookin’ diffs with diff-highlight and more
* [github-cheat-sheet](https://github.com/tiimgreen/github-cheat-sheet): A list of cool features of Git and GitHub
* [git tips](https://github.com/git-tips/tips): Most commonly used git tips and tricks
* [Little Things I Like to Do with Git](https://csswizardry.com/2017/05/little-things-i-like-to-do-with-git/)