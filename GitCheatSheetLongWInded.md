### 1) Starting to "track" an existing project (Locally only no web yet!)
Gitese.
First word is *"Tracking"*
Rough def:
*Tracking* -- to make local git software aware of some files in a directory. Just locally. I won't discuss posting to the web till section 2.
That is at the Bash prompt. Maybe not all of these things, but this is what GIT says.
The scenario: You've got some stuff  on your computer you want (eventyally) to share on GIT on the web. Say its in the directory:
```
~/ProjectBoffo # go to the directory
```
where you have exactly two R program files you want to add:

```
$ls  ~/ProjectBoffo
>boffo1.R boffo2.R
```
I'll call this directory the locRepoDir for Local Repository directory.
The files in this directory are like prospective players on a high-school tiddlywinks team before the team is even started. The first thing to do is start a new team.
  Go to Terminal (Bash prompt) and type:
```
cd ~/ProjectBoffo
$ git init  # initializes the .git
```
This creates a new team, but there are no players on the roster yet. We can fix that like this:

```
$ git add *.R # adds  all the R files
```
Now let's check the status of the new players.
```
$ # Next command will display what Git (and all the other cool kids) thinks is important, "status"
$ git status
```
What we see on the screen is (after trimming some generous linespacing):
```
On branch master
Initial commit
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   boffo1.R
	new file:   boffo2.R
```
Gitese: ***commit***
Even though the files have been 'added' to the roster so are *tracked* by Git, they're not yet 'starters'. They're just bench warmers for the moment. The squad. They're just practice players warming the bench.  To promote them to the starting we have to `commit` them to the program. This will make the newly
```
# The Unixian -m  flag stands for "message"
$ git commit -m 'initial project version'
```
 ######[........See Note 1: What's created with initialization and first commit.]

You can check what's been done via:
```
$ git status
```
Then git tells me everything is cool by it:
```
On branch master
nothing to commit, working directory clean
```
######[.......But see Note 2: Other stuff floating around on initial commit.]






```
git status
```
**So far, everything's still local. (In Gitese, nothing's *tracked*. See later.)**

Now lets add another file.
Let it be standard Github README file.
Create one one up in a text editor and save it in the *locRepoDir* (here:  ~/ProjectBoffo).
If you check for it now,

Then add it to the git so local git will track it.
```
git add README
```
Remember, if you want git not to compain, then you should also issue another `commit` command. Maybe something like
`commit README -m 'commit including new README'`


Now to get something "posted" to github ( Git:"get things tracking" a.i.w.)

###Tracking New Files###
To get the 3 files "tracking" on Github website, do the following

$ git add README

If you run your status command again, you can see that your README file is now tracked and staged:

$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   README

You can tell that it’s staged because it’s under the “Changes to be committed” heading. If you commit at this point, the version of the file at the time you ran git add is what will be in the historical snapshot. You may recall that when you ran git init earlier, you then ran git add (files) — that was to begin tracking files in your directory. The git add command takes a path name for either a file or a directory; if it’s a directory, the command adds all the files in that directory recursively.

###Notes
Note 1).  What's created with initialization and first commit
From the website:
>This creates a new subdirectory named .git that contains all of your necessary repository files — a Git repository skeleton. At this point, nothing in your project is tracked yet. (See Chapter 9 for more information about exactly what files are contained in the .git directory you just created.)

Note 2).  **Other stuff on initial commit.** If there had been other files hanging around in the file beyond the things that  been properly `add`-ed **before** the `commit`, teh `git status` command   would have complained and given me some info about them. The same is true if any files that had been `add`-ed had been changed without a fresh `commit` .
>If you want to start version-controlling existing files (as opposed to an empty directory), you should probably begin tracking those files and do an initial commit. You can accomplish that with a few git add commands that specify the files you want to track, followed by a commit:
$ git add *.c
$ git add README
$ git commit -m 'initial project version'




ON cloning:
From website:
>Cloning an Existing Repository

>If you want to get a copy of an existing Git repository — for example, a project you’d like to contribute to — the command you need is git clone. If you’re familiar with other VCS systems such as Subversion, you’ll notice that the command is clone and not checkout. This is an important distinction — Git receives a copy of nearly all data that the server has. Every version of every file for the history of the project is pulled down when you run git clone. In fact, if your server disk gets corrupted, you can use any of the clones on any client to set the server back to the state it was in when it was cloned (you may lose some server-side hooks and such, but all the versioned data would be there — see Chapter 4 for more details).

You clone a repository with git clone [url]. For example, if you want to clone the Ruby Git library called Grit, you can do so like this:

$ git clone git://github.com/schacon/grit.git

That creates a directory named grit, initializes a .git directory inside it, pulls down all the data for that repository, and checks out a working copy of the latest version. If you go into the new grit directory, you’ll see the project files in there, ready to be worked on or used. If you want to clone the repository into a directory named something other than grit, you can specify that as the next command-line option:

$ git clone git://github.com/schacon/grit.git mygrit

That command does the same thing as the previous one, but the target directory is called mygrit.

Git has a number of different transfer protocols you can use. The previous example uses the git:// protocol, but you may also see http(s):// or user@server:/path.git, which uses the SSH transfer protocol. Chapter 4 will introduce all of the available options the server can set up to access your Git repository and the pros and cons of each.
## Editorial git is great but...
Documentation and tutorial manuals is very difficult business. The pros will laugh while the newbies are less than baffeled almost nomatter what you do. The gang in between may have the hardest lot of all to please. "I know I did this once, but what did I ned to do?"

To try to find out, we may find ourselves bounding mercilessly between two ends of of the spectrum:
Infrared:  The brilliant YouTube pre-teen (who hasn't been to Toastmasters) telling us too much about nothing  (how cool everything is and all the things you can do) and then slipping some very important notes past me before I can hit pause.

UltraViolet: The techie who ill-spent his youth reading Unix man pages from the 1970's (or maybe one who wrote the same).


There are many instances of course where there is lots of visible light.
One is this page: http://git-scm.com/book/en/v1/Git-Basics-Getting-a-Git-Repository.

  But Git is still more complicated than it should be. If you have an app with  pretty decent guis, it shouldn't be necessary form to go  a *Bash* prompt
to do  my updating (though I would like the option to be there)
