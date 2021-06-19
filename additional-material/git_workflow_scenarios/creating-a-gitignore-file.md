# .gitignore

The .gitignore file is a text file that tells Git which files or folders to ignore in a project.

A local .gitignore file is usually placed in the root directory of a project. You can also create a global .gitignore file and any entries in that file will be ignored in all of your Git repositories.

## Why .gitignore
Now you may wonder why would you want git to ignore certain files and folders. Its because you don't want files like build files, cache files, other local configuration files like node modules, compilation files, temporary files IDE's create, etc to be tracked by git. It's usually used to avoid committing transient files from your working directory that aren't useful to other collaborators.

## Getting started
To create a local .gitignore file, create a text file and name it .gitignore (remember to include the . at the beginning). Then edit this file as needed. Each new line should list an additional file or folder that you want Git to ignore.

The entries in this file can also follow a matching pattern.

```
* is used as a wildcard match
/ is used to ignore pathnames relative to the .gitignore file
# is used to add comments to a .gitignore file

This is an example of what the .gitignore file could look like:

# Ignore Mac system files
.DS_store

# Ignore node_modules folder
node_modules

# Ignore all text files
*.txt

# Ignore files related to API keys
.env

# Ignore SASS config files
.sass-cache

```
To add or change your global .gitignore file, run the following command:

```
git config --global core.excludesfile ~/.gitignore_global

```
This will create the file ~/.gitignore_global. Now you can edit that file the same way as a local .gitignore file. All of your Git repositories will ignore the files and folders listed in the global .gitignore file.

## How to Untrack Files Previously Committed from New Gitignore

.gitignore will prevent untracked files from being added (without an add -f) to the set of files tracked by git, however git will continue to track any files that are already being tracked.

To stop tracking a file you need to remove it from the index. This can be achieved with this command.

git rm --cached <file>
If you want to remove a whole folder, you need to remove all files in it recursively.

git rm -r --cached <folder>
The removal of the file from the head revision will happen on the next commit.

WARNING: While this will not remove the physical file from your local, it will remove the files from other developers machines on next git pull.
