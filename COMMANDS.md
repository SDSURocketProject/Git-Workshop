# Git Commands

This file contains a brief summary of some of the key commands for using Git

Syntax:

`<text>` refers to a required parameter.

`[text]` refers to an option parameter.

Paramter requirements can be nexted. ex: `[parameter 1 <parameter 2>]`

In the above case, parameter 2 is required if parameter 1 is specified.

## git-pull

```
git pull						# fetch commits from remote and merge them into local
```

## git-push

```
git push						# push commits to remote

git push [-u origin] <branch>	                        # set upstream to origin and push to <branch>. Useful for first push on new branch
```

## git-add

```
git add	<path>					        # stage file or directory at <path> for commit
```

## git-commit

```
git commit						# create a commit. Text editor will be opened to type commit message

git commit [-m <message>]		                # create a commit with the message <message>. Multiple -m parameters can be used

git commit [-S]					        # create a commit, and gpg sign it. Can only be used if gpg is configured with gitlab

git commit [-S] [-m <message>]	                        # create a commit with a specified message, and gpg sign
```

## git-branch

```
git branch						# list all local branches

git branch [-a]					        # list all branches, including remote branches

git branch <branchname> [base]	                        # create a new branch with name <branchname> from the point [base]
						        # [base] can be a branch name, commit hash, etc

git branch -D <branchname>		                # delete the branch <branchname>
```

## git-checkout

```
git checkout <branchname>		                # switch from the current branch to <branchname>

git checkout <commit>			                # create a temporary instance at <commit>

git checkout -- <path>			                # undo changes to <path> since last commit
```

## git-clone

```
git clone <url> [path]			                # clone the repo at <url> to [path]. If [path] is not specified, the path will
						        # be generated from the repo name
```

## git-diff

```
git diff						# show changes to all tracked files since last commit

git diff [path]					        # show changes to [path] since last commit

git diff [commit] [path]		                # show changes to [path] since [commit]
```

## git-status

```
git status						# show status of staged, unstaged, and untracked changes
```

## git-log

```
git log							# show log of all commits and branches

git log [--graph] [--oneline]	                        # show log with graph of branches and summarize commits to one line
```

## git-cherry-pick

```
git cherry-pick <commit>		                # apply <commit> (even if from another branch) to current working tree
```

## git-reset

```
git reset --soft HEAD^			                # undo the most recent commit

git reset --hard				        # reset working tree to last commit, discarding changes

git reset --hard HEAD~<N>		                # undo <N> most recent commits. ONLY USE IF THOSE COMMITS ARE NOT PUSHED
```

## git-revert

```
git revert HEAD~<N>				        # create a commit that undoes <N> most recent commits

git revert <commit>				        # create a commit that undoes commits back to <commit>
```
