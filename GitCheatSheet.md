# Git cheat sheet (reference card) for Mac OS X
### OR: Things I had to look up between uses and was afraid to ask
For sources, see end of this document.
### Glossary
> ###Gitese. Terms used by git all the time:
>To ***initialize*** a directory: via $ git init; Lets git know the local directory exists  
To ***stage*** a file: via $ git add; Tells git you've changed a file usually because likely be commiting it.  
To ***commit*** a local repository; Tells git that all the pending 'staged' files are ready to be made official latest version of the git.  
To **push** last commited changes to the GIthub Web repository.  
A ***README*** file. It must be called this (or README.md for markdown files).The file in the local git directory that will be the 'guide' document on the Git Web Repo for yourproject.
### Other notation used here:
***Local git directory*** : where a project is kept locally and where changes are made to your project using ordinary tools
*** Github Web Repo *** a place on the Github server farm where your project can be 'published'.  
***'[SomeName]'*** indicates an arbitrary name or text chosen by user.
Mostly such things will indicate local directory names, local filenames or
Github Web repository names. The labels will remain stable when they refer to the same thing as a previous usage. So two occurrences of ['LocalDirA'] will refer the same directory. While '[LocalDirB]'will be a different one.  
***Special rubric comments on git and other terminal commands*** Some comments will be added after terminal commands with
` $ command #-- This is a special rubric comment: do not type it` They aren't part of the commands and should NOT  be typed.  



### Step 0) Register with Github, Download and install Git if you haven't already
Registering is easy as I recall, but I lost the instructions.
```
git config --global user.name '[User's name (or aka?)]'
git config --global user.email '[User's email address]
```

### Step 1) Get a new Github Web  repository for a new project if you need one.
Go here: https://github.com/  
You'll see something like this (only prettier). Pick the link shown:
 ```
 Welcome to GitHub! What's next? (on Aug 9, 2012)
    * Create a repository <---- PICK ME
    * Tell us about yourself
    * Browse interesting repositories
    * Follow @github on Twitter
```
Give your new Github Web Repository a name in the next window


### Step 2) Establishing link between a local directory  and a GitHub Web Repo for the first time
Assume I've created a Github Web Repo in Step 1 and called it  ***'[NewProject]'***


Thie files for this project will be in the ***local*** directory called:  ***'[NewProjectDirectory]'***

#### Step 2a.  Navigate to the local git directory
Everything git does with this project on your machine will happen here.
```
$ cd '[LocalGitProjectDirectory]'  
```
#### Step 2b. Initialize the git. Let git know it will be managing the local directory.
```
$ git init  #-- initialize a local diectory as a git directory
```
#### Step 2c prepare (gitese 'stage') any files for initial 'commit'.
(See glossary at top of this document.)
Here I'll just create an empty README file. This will become the summary info file on the Github Web repo when you finally post it. This is NOT a git command, just vanilla unix.
```
$ touch README  #-- creates an empty README file a local diectory as a git
 directory
 ```
 Step 2d make git aware
 ```
$ git add README  
```
Now m
$ git commit -m '[CommentForFirstCommit]'  
$ git remote add origin 'github@github.com:['UserGithubName']/'[NameOf Github WebRepo>].git'  
git push origin master
```
## Revising local directory to existing Github Web Repo
Some time later, suppose you make chagnes
Go to local directory and make your changes normally.
```
cd '[Existing local repository already posted at least once to Github web]'
# [[User create/edits file newfile.txt]]
```
There are 3 steps after you've made your local changes.
```
# step 1- alerts git of changes ('stages/adds' them)
git add newfile.# 'stages the file'
# step 2- makes the changes the OFFICIAL version (commits them)
git commit -m '[comment sketching your changes]'
# step 3 -- push
git push
```
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




This is based and may  include  excerpts from:  
[[1]] http://git-scm.com/book/en/v1/Git-Basics-Getting-a-Git-Repository
and  
[[2]] https://guides.github.com/introduction/getting-your-project-on-github/
and
## Really short version after [[3]]
[ConnorD/ Youtube video](http://www.google.ca/url?sa=t&rct=j&q=&esrc=s&source=web&cd=5&cad=rja&uact=8&ved=0CDQQtwIwBA&url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DTPY8UwlTIc0&ei=TvtcVJWzFoW3yQTehIDYCQ&usg=AFQjCNEwXnVBg5ZrHl4oPcfkPGvyPieyTw&bvm=bv.79184187,d.aWw)
