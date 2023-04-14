# A simple introduction to git


## The short version

To setup a new repository, you go to the folder you want to manage and:

```
git init
```

Then use your favourite editor and create a file .gitignore, which lists all files that you want git to ignore. This could be a long list depending on your environment, but usually you have content like:

```
venv/ 
__pycache__/
.idea/
```

There is a nice template at [Python.gitignore](`https://github.com/github/gitignore/blob/main/Python.gitignore`) where you can pick what is suitable for you. [gitignore.io](https://gitignore.io) is also a good reference.


When git is setup correctly, this is what you do every day:

```
git pull    # get latest changes from repository
**do some work**
git status  # to see what you have done
git diff    # if you want to inspect the diff to see in detail what you have done
git add .   # "stages" all files into a commit (a set of changes).
            # you could also add files one by one if you like!
git commit -m "My comment about the commit"  # add a useful comment
git push    # will push the changes to a remote location (probably __github__)
```

if you already know what changes you have done, you can skip the git status and git diff.

hint: when I do minor stuff or are in a hurry, I enter the commit comment "wip" for "work-in-progress". But the better you write the comment, the better for all future readers.


If you desperately need a GUI (I sometimes do, but not often) I can recommend GIT KRAKEN, a very nice GUI client for git.





## The long version

Git is a distributed source code manager (SCM). The difference against other SCMs that are server-based, is that there is __no server__ involved!  All nodes are equal, and you can clone a repository from any other node you have access to.

Basically you can have two nodes that push and pull updates between them. 

However its more normal to have one node as the "super-node". Ususally one uses __GitHub__ or __GitLab__ for this 'always-on' service.

### Commits

The smallest atom in the git universe is a "commit". A commit consists of __a set of changes to files__.

The history of a file in a git repo is therefore a list of commits that eventually ends up as the current file state.

Every commit is linked back and forth. It can be a good mental picture to visualize a linked list of commits.





## Installation

```
sudo apt install git
```

## First use

This instruction assumes there is a folder ./myproject  in my home directory. 

There I have one file app.py and have also created a virtual environment. I have also created a requirement.txt using pip.

```
pip freeze > requirements.txt
```

This folder now contains the following:

```
>ll
total 12
drwxrwxr-x  3 peter peter 4096 Mar 23 08:54 ./
drwxr-xr-x 89 peter peter 4096 Mar 23 08:54 ../
-rw-rw-r--  1 peter peter    0 Mar 23 08:54 app.py
-rw-rw-r--  1 peter peter   78 Mar 23 08:55 requirements.txt
drwxrwxr-x  5 peter peter 4096 Mar 23 08:54 venv/
```

> Initialize git for this folder

```
git init
```

> A folder .git is now created

```
>ll
total 20
drwxrwxr-x  4 peter peter 4096 Mar 23 10:02 ./
drwxr-xr-x 89 peter peter 4096 Mar 23 08:54 ../
-rw-rw-r--  1 peter peter    0 Mar 23 08:54 app.py
drwxrwxr-x  7 peter peter 4096 Mar 23 10:02 .git/
-rw-rw-r--  1 peter peter   78 Mar 23 08:55 requirements.txt
drwxrwxr-x  5 peter peter 4096 Mar 23 08:54 venv/
```

You can issue a status command whenever you want.

```
>git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	app.py
	requirements.txt
	venv/

nothing added to commit but untracked files present (use "git add" to track)
```

Next step is to add a __.gitignore__ file, since we dont want everything to be versioned

You can create this file yourself by:

1) do a git status
2) See if any unwanted files would be staged, else continue
3) Add that unwanted folder/file/path to .gitignore
4) goto 1)

You could also download a prefrabricated .gitignore files, or use gitignore.io to create one.

## Workflow

The general workflow is:

work area  --> add to staging area --> commit  --> push to remote repository

* Work area is your normal set of files
* You add single files or "all" (using .) to say "these files will be part of the commit"
* You can do the "git add" as many times as you like
* You do git commit -m "My message"

Use "git status" often to check the state.

Remember that a **commit** is a set of files. You cant extract ONE file from the set, but have to consider the set as a unit.


## Reversing

If you make a mistake, it is easy to take a step back.

__However, it is also easy to make a complete mess out of git, so in the beginning, keep a local copy of your source files too!__

## Un-staging a file

If you accidentally have "staged" a file, maybe using "git add ." and see that you have staged all files in the venv/ subdirectory, you can unstage them by:

```
git reset <file>
```

If you want to unstage ALL files, do:

```
git reset
```

## Un-committing a file

If you have staged and committed (but not pushed) it is a little more tricky to get out of the situation.



