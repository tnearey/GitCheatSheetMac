# Git cheat sheet (reference card) for Mac OS X
### OR: Things I had to look up between uses and was afraid to ask

#### See editorial near end
This is based on and contains excerpts from:
http://git-scm.com/book/en/v1/Git-Basics-Getting-a-Git-Repository

## L As of 6 Nov 2014 at least somethings need to be done by hand in Bash/Dariwn

## Stage 1: Local repository only: Creation, 'tracking' and 'committing'
There are 3 basic commands here:  
1. `git init` to initialize a local repository
2. `git add <filename or filenamePattern>` This can do one of two things:
  1.  Make Git aware of new files ( to start to 'track' them).  
  2.  Prepare (Gitese:)'stage') for committing any previously added files you  have **modified** since the last `commit'3
  . `git commit -m 'You must put a comment here'` to install  any changes or additons to the official 'latest version.'



A little more detail: Basic steps when you have a new directory (short version)
Suppose you've got a couple of local files you want to put up on Git on the web.
Git knows nothing about them yet even locally.

```
$ cd ~/ProjectBoffo # go to the directory -- this will be the local repository
$ ls ~/ProjectBoffo # see what's there
boffo1.R boffo2.R
```
First off we need to make Git locally aware of the project.
```
cd ~/ProjectBoffo
# Next command lets  Git know you're starting a local repository in .
$ git init  # initializes the .git
```
Now it's a project without any source files. We need to make Git aware of some files
by issuing an `add` command.
```
# Next one adds the two R files - makes them  be 'tracked' by GIT
$ git add *.R
```
Now check status from Git's perspective;
```
$ git status
```
and receive back:
```
On branch master
Initial commit
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   boffo1.R
	new file:   boffo2.R
  ```
  The files from the `add` command are  now said in Gitese to be **tracked** but they haven't been **committed**
  (they're not promoted to the starting squad yet). To promote them to latest and greatest, we have to `commit` the changes.

```
# The Unixian -m  flag stands for "message"
$ git commit -m 'initial project version'
```
You can check what Git thinks has been done via:
```
$ git status
```
Which yields the soothing
```
On branch master
nothing to commit, working directory clean
```
If there had been other files in the directory that hadn't been udergone `add` yet,
or if we had changed one of the previously added files before a fresh `commit`, then `git status` would have let us know about it.

Now if you edit boffo1.R and make some changes, you can make the changes only by 'stick'
by issuing a fresh  `commit`.
```
git commit -m 'A new message after the last change'
```

##Stage 2. Posting to the web
