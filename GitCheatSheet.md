# GitHub cheat sheet (reference card) for Mac OS X
### OR: Things I had to look up between uses and was afraid to ask
For sources, see end of this document.
Also see https://guides.github.com/introduction/getting-your-project-on-github/
for the desktop version (some notes on that are interspersed  in this document).
This repository also contains a couple of annotated screenshots of the GitHub Desktop App that may be helpful.

[ScreenShot1](https://github.com/tnearey/GitCheatSheetMac/blob/master/GitHub_DesktopApp_Mac_7Nov2014Page1.png)  
[ScreenShot2](https://github.com/tnearey/GitCheatSheetMac/blob/master/GitHub_DesktopApp_Mac_7Nov2014Page2.png)

### Glossary
> ###Gitese. Terms used by git all the time:
>To ***initialize*** a directory: via $ git init; Lets git know the local directory exists  


>To ***stage*** a file: via $ git add; Tells git you've changed a file usually because likely be commiting it.  


>To ***commit*** a local repository; Tells git that all the pending 'staged' files are ready to be made official latest version of the git.  


>To **push** last commited changes to the GIthub Web repository.  
>file in the local git directory that will be the 'guide' document on the Git Web Repo for yourproject.


### Other notation used here:
> ***Local git directory*** : where a project is kept locally and where changes are made to your project using ordinary tools


> *** Github Web Repo *** or *** Remote Repository *** a place on the Github server farm where your project can be 'published'.  


> ***'[SomeString]'*** indicates an arbitrary stretch of text in single quotes chosen by user.

> ***'[[SomeLocalDirectoryOrFileName]]'***  with double square brackets is a string that represents a  user's local directory name or file name.

> ***'{{SomeRemoteRepositoryName}}'***  with double curly braces is a string that represents the name of a remote repository. The [[]] and {{ }} aren't typed, they're just semantic decoration to keep straignt what name is refering to a local object and what is refering to something on the web.

> The labels will remain stable when they refer to the same thing as a previous usage. So two occurrences of ['LocalDirA'] will refer the same directory. While '[LocalDirB]'will be a different one.

> Your local project directory,  say '[[ExampleDemoProject]]' typically has to match names with the remote directory name ''{{ExampleDemoProject}}' '


>***Special rubric comments on git and other terminal commands*** Some comments may be added after terminal commands with a special 3 charcter sequence #--  
` $ command #-- This is a special rubric comment: do not type it`  
 They aren't part of the commands and should NOT  be typed.  



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
There are a lot of small steps to this. Assume I've created a Github Web Repo in Step 1 and called it. ***'{{ExampleDemoProject}}'***  
The files for this project will be in the ***local*** directory called:  ***'[[ExampleDemoProject]]' ***  

#### Step 2a).  Navigate to the local git directory ####

```
$ cd '[[ExampleDemoProject]]'  
```
Everything git does with this project on your machine will happen here.

#### Step 2b. Initialize the git. Let git know it will be managing the local directory.
```
$ git init  #-- initialize a local diectory as a git directory
```
>[ With the GitHub dDesktop APP you can do the equivalent of Steps 2a and 2b by dragging the '[[ExampleDemoProject]]' to the big blank rectangular area of the app. ]



#### Step 2c): Prepare (stage) any files for initial commit.
(See glossary at top of this document.)
Here I'll just create an empty README file. This will become the summary
info file on the Github Web repo when you finally post it.
This is NOT a git command, just vanilla unix.

```
$ touch README  #-- creates an empty README file in the local directory as a git
 repository
 ```

 #### Step 2d: Make git aware of the new file ('stage' the file by the add command )
 ```
$ git add README  
```
Git now knows this file is ready to be committed (see next step).

#### Step 2e): Execute the initial commit
```
$ git commit -m '[CommentForFirstCommit]'  
```
This tells git that you're serious about committing all the files that
you've staged (via add command) since your last commit (or from scratch asin this case).




### Step 2f): Help git establish a relationship between your local directory and the GitHub Remote Repo.
```
git remote add origin 'github@github.com:['UserGithubName']/'[NameOf Github WebRepo>].git'
```
This only has to be done once. Git will keep track of this link in this directory

> [ IN the GitHub Desktop APP, you can make the link between the local and remote repositories at the first step when you find or create a Local Repository and a name for the project in the Remote Repository. Use the + button at the upper left]


### Step 2g): Push (publish) the last committed changes to the remote Github Reposatory
```
git push origin master
```
After this initial push, the command will simply be `git push`





## 3) Making changes in the local repository and publishing to existing Github Remote Repository

Preliminary: Non-git work. Suppose you turn off your computer for the night. The next day,  you make changes to the README file (which was an empty file till now.)
You also create a new test file  file '[SomeNews.txt]' with a paragraph of news in it.
Both these files are now in the   '[[ExampleDemoProject]]' directory, the Local Repository where, where the README file is located.
Go to local directory and make your changes normally.



```
$ cd '[[ExampleDemoProject]]'
```

There are 3 substeps steps after you've made the local changes to the two files.```


### step 3a): Notify git of changes ('stage' the files) via `git add`
```
git add README
git add  '[SomeNews.txt]'
```


#### Step 3b):- makes the changes the OFFICIAL version via `git commit`
'''
git commit -m '[comment sketching your changes]'


### Step 3c -- Publish the changes to the Remote Repository via `git push`
```
git push
```
Note that no other arguments are necessary in this case



Reference; This is based on information in:
[[1]] http://git-scm.com/book/en/v1/Git-Basics-Getting-a-Git-Repository
and  
[[2]] https://guides.github.com/introduction/getting-your-project-on-github/
and [[3]]
[ConnorD/Youtube video](http://www.google.ca/url?sa=t&rct=j&q=&esrc=s&source=web&cd=5&cad=rja&uact=8&ved=0CDQQtwIwBA&url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DTPY8UwlTIc0&ei=TvtcVJWzFoW3yQTehIDYCQ&usg=AFQjCNEwXnVBg5ZrHl4oPcfkPGvyPieyTw&bvm=bv.79184187,d.aWw)
