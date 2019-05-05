# Git-Workshop Instructions

These instructions will run through a series of steps:

1. Cloning a repo
2. Creating a new branch
3. Creating a file
4. Staging the file for commit
5. Creating a commit
6. Pushing the commit
7. Creating a merge request

## Cloning a Repo

To clone a repo, use the command:

```
git clone <url> [destination]
```

where `<url>` is replaced with the url of the repo you want to clone, and `[destination]` is the name of the
directory you want to clone the repo to. The `[destination]` field is optional, and if it is not specified the
name will be the same as in the url.

You can find the url my clicking on the blue clone button on the main page of a repo.
It will list two URLs, one for http, and one for ssh. You can only use the ssh url if you have an ssh keypair
associated with your account, so use the http url.

For this activity, run:

```
git clone http://git.sdsurocketproject.org/avionics/Git-Workshop.git workshop
```

This will clone the repo to a new directory named `workshop`. Go into it now.

## Creating a new branch

### Creating the branch

Creating a new branch uses the format:

```
git branch <branch-name> [start-point]
```

where `<branch-name>` is the name of the branch you want to create, and `[start-point]` is an optional
parameter referencing the desired start point of the branch, given as a branch name or commit hash. If no
start point is given, it will assume the most recent commit of the current branch.

You can also list all branches with the command:

```
git branch -a
```

If you are not seeing a branch you expect to, update your repo with a pull:

```
git pull
```

For this activity, run:

```
git branch <your first name> master
```

to create a new branch off master with your first name.

### Entering the branch

Now that you've created the branch, you've got to switch over to it.

This is done with the command:

```
git checkout <branch-name>
```

## Creating a file

You can create a file using any text editor, IDE, or any other program of your choice. You can also create
a new empty file using the command `touch <filename>`.

Create a file with your username as a filename. Make sure to make the capitalization the same.

Inside the file, type a short bit of text (it can be anything you want).

## Staging a file for commit

### Viewing Changes

There are two main ways to view changes you have made.

```
git status
```

will show a list of what files are staged for commit, modified but not staged, or modified and not tracked.

```
git diff [filename]
```

will show a line-by-line readout of all changes made in non-staged files. It can be filtered to a single file
by specifying `[filename]`.

### Staging Changes

To stage a change for commit, use the command:

```
git add <path>
```

Where `<path>` is a directory or file. If you specify a directory, all its contents will be staged. In
general, it is better to specify each file individually to avoid accidentally staging something unwanted,
such as a log file or build object.

Stage your file for commit with the following command:

```
git add <your filename>
```

### Unstaging Changes

If you have staged a file you didn't mean to stage, you can unstage it with the following command:

```
git reset <filename>
```

## Creating a commit

### Creating the commit

To create a commit from the staged changes, run the following command:

```
git commit [-S] [-m <message>]
```

Running `git commit` by itself will create a commit by itself, and open your text editor to enter a commit
message.

Running with the `-S` option will GPG-sign your commit. Only use this if you have GPG configured and your
public key associated with your git account.

Running with the `-m [message]` option will allow you to specify the commit message without dealing with
a text editor. Put your message inside single quotes. Additional `-m` options can be used for a multi-line
commit message.

For example:

```
git commit -S -m 'Main title of the commit' -m 'Second line of the commit' -m 'third line'
```

Only one line is required for a commit message.

The first line of a commit message should be short and concise, but not so short as to be vague.

Examples of good commit messages:

```
# changed beep to for seconds for overpressure

# add thermocouple conversion function

# added textbox for filename input
```

Examples of **bad** commit messages

```
# edit code

# minor appearance changes

# maybe this one works
```

_(all of the above examples are real commits from the ACS-RS and OBC-GUI repos)_

### Undoing the commit

To undo the most recent commit (any only the most recent commit), and leave the working tree untouched,run the
following:

```
git reset --soft HEAD^
```

To reset the working tree to how it was at the last commit, discarding any changes to tracked files:

```
git reset --hard
```

To undo changes to a single file since the last commit:

```
git checkout -- <file>
```

To undo the most recent N commits, and remove them forever, run the following:

```
git reset --hard HEAD~N
```

Be sure to replace `N` with the number of commits you want to undo. **do NOT do this to any pushed commits**.

If you need to revert a pushed commit, run the following:

```
git revert HEAD~N
```

The difference between reset and revert is that revert creates a commit that removes other commits, allowing
you to push the removal to other users.

## Pushing the commit

To push the commit to the server, run the command:

```
git push
```

If you used ssh to clone the repo, you will be prompted for the password on your ssh keypair, if you have one
set. If you used http, you will be prompted for your username and password. Nothing will be displayed when you
type your password, not even asterisks, so don't be worried about nothing being typed.

The first time you push on a branch (but not on any subsequent pushes **to that branch**) you must run the
following as your push command:

```
git push -u origin <branch name>
```

If you are editing files that someone else may have edited, be sure to pull before you push, to avoid merge
conflicts on the remote server.

## Creating a Merge Request

You're now done with the commandline portion of the activity.

To create a merge request, follow these steps on the GitLab Website:

1. Click the "Merge Requests" button on the left side
2. Click the "New Merge Request" button on the upper right
3. Set the Source Branch and Target Branch accordingly. For this activity, the source branch is the one you
just made, and the target is master.
4. Click "Compare branches and continue"
5. Set the Title to a brief description of what you did. EX: "Add Feature X"
6. Write a description for your merge request. This can be as detailed as you like, and should act as a
summary of the commits in the merge request
7. Set the assignee(s). The assignees should include yourself and anyone else responsible for what you edited
8. Set the milestone(s). Select any milestone(s) that your merge request addresses. It may not address any
9. Set the label(s). Select any labels that describe your merge request
10. Ensure that "Delete Source Branch" and "Squash Commits" are unchecked
11. Submit Merge Request
12. Once all assignees have approved the merge request, a maintainer can merge the merge request
