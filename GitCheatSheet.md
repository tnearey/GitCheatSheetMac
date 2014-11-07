# Git cheat sheet (reference card) for Mac OS X
### OR: Things I had to look up between uses and was afraid to ask

#### See editorial near end
This is based on and contains excerpts from:
http://git-scm.com/book/en/v1/Git-Basics-Getting-a-Git-Repository
## Really short versionafter ConnorD/ Youtube video.
### Download and install Git:
git config --global user.name "<User's name or aka>"
git config --global user.email "< User's email address >"
### Commiting a local directory
cd '<Git Local Repository Directory>'
git init
touch README
git add README
git commit -m '<Comment for first commit> '
git remote add origin 'github@github.com:<User's Short Github Name'>/'<Name of repository on Github Web>.git'
git push origin master
## Revising existing (modified) local directory to existing Github Web repository
cd '<Existing local repository already posted at least once to web>'
git remote add origin 'github@github.com:<User's Short Github Name'>/'<Name of repository on Github Web you are updating>.git'
git push origin master
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

This can be done initially the GitHub app, but it's not obvious  
1) Start GitHub app.
2) Navigate to main menu item: [ Apple ] **[File]**  
  ---- [GitHub Main menu]: File: Open Local Repository: *< choose directory manually >*  
3) Navigate to main menu item:  [ Apple ] [File] [Edit] [View] **[Repository]**
        ---- [Github Main Menu]: Repository : Push  
  Then you'll see it in the left panel and can right click to see it on the GitHub web.  
  Now big question is how to revise.
