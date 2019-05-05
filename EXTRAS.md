# Git Extras

This is a compilation of useful git tips and tricks

## Merge Conflict Resolution

If you get a warning about merge conflicts when performing a merge or pull, running `git status` will show
what files contain conflicts.

### manual conflict resolution

At each case of an error (there may be more than one per file) there will be a block structured like this:

```
<<<<<<< HEAD
foo1
=======
foo2
>>>>>>> branchname
```

In this, the section between `HEAD` and `=======` are the contents of that section from the HEAD (the current branch)
and the section between `=======` and `branchname` are the contents from the branch being merged in.

To resolve, open the file in an editor and delete all portions of the block you do not want. For example,
if we want to keep the version from `HEAD`, we would change the block to be:

```
foo1
```

Then we run `git add <filename>` to mark the conflict as resolved and create a commit.

## gitignore

Each repo can have a file named `.gitignore` in its base directory.

This file can be used to list files, directories, and filetypes that will be ignored by git.
This is useful for preventing files such as log files, build objects, etc from cluttering up the output of
`git status` or from being staged for commit.

To use it, simply list what you want to ignore, one entry per line. `*` acts as a wildcard and `!` as a not.

Here is an example file for a C/C++ project:

```
*.o				# ignore .o build objects
*.csv			# ignore .csv log files
my_binary		# ignore file named by_binary
!my_binary/		# but not the directory named my_binary
Makefile		# ignore the Makefile
moc_*			# ignore anything starting with moc_
```
