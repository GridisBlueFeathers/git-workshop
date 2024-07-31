# JUL 2024 Piscine Git Workshop

## Table of Contents
- [What is Git?](#what-is-git)
    - [What is a version control system](#what-is-a-version-control-system)
- [What is a repository](#what-is-a-repository)
- [Tracking](#tracking)
- [Staging area](#staging-area)
- [Commiting](#commiting)
- [Rinse and repeat](#rinse-and-repeat)
- [Pushing to a remote repository](#pushing-to-a-remote-repository)
    - [Connecting SSH keys](#connecting-ssh-keys)

## What is Git?
**Git** is a **version control system**. According to the creator of Git and what is written in Git's own repo's first commit
```
GIT - the stupid content tracker

"git" can mean anything, depending on your mood.

 - random three-letter combination that is pronounceable, and not
   actually used by any common UNIX command.  The fact that it is a
   mispronounciation of "get" may or may not be relevant.
 - stupid. contemptible and despicable. simple. Take your pick from the
   dictionary of slang.
 - "global information tracker": you're in a good mood, and it actually
   works for you. Angels sing, and a light suddenly fills the room. 
 - "goddamn idiotic truckload of sh*t": when it breaks
```

### What is a version control system?
A **version control system** is a **system** that **controls versions** of your project. So that, for example, if your project got a new feature, and it started to break something, it would be possible to go back to a stable version.

### Why use Git
Git is very verbose. On each action Git usually gives a lot of information on what just happened, or if **Git** doesn't like something, it usually would output the problem desctiption and potentially how to solve it.
Git also makes collaboration on projects easier through branches and merges.

## What is a repository?
On a basic level, a repository is just a directory on a computer, that has `.git` subdirectory in it. `.git` directory is a storage of commits and other information that **Git** tracks.

There are two methods to create a repository:
- `init`ialise a repository in a directory
- `clone` an existing **remote** repository

Once you have your repository, you can start adding files to it

## Tracking
One of the main things that **Git** does is tracking files, and changes in files. If you just `init`ialised a repository it won't have any files that **Git** would track, so when you add a file to your **working directory** and do `git status`, you will see a message like:
```
Untracked files:
    (use "git add <file>..." to include in what will be committed)
        new_file
```

In order to start tracking changes in a file, you will need to add it to the **stagind area**, this is done using `git add <file>` command.

## Staging area
**Staging area** is a middleground between your files being just raw files without any kind of history and changes in your files being compiled in a **commit**. When you `git add`ed some files, you will be able to see what will be compiled in a **commit** using `git status` again.
```
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   new_file
```

## Commiting
Now, we are ready to create a **commit**. Run `git commit -m <meaningful message>` command, and you will see a following message:
```
[master (root-commit) 80a3cb8] initial commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 new_file
```

In this message you can see `master` is a name of a branch in which we created this **commit**, `(root-commit)` which means that there were no previous commits in this repository, `80a3cb8` or most likely some other hash of your commit, `initial commit` is a commit message that you left, `1 file changed, 0 insertions(+), 0 deletions(-)` is what happened since the last commit and `create mode 100644 new_file` is more detailed file by file description of what actually changed.

After you **commited**, if you would try to do `git status`, you will see this:
```
On branch master
nothing to commit, working tree clean
```

It means that since the last commit there were no changes to tracked files, and that there are no new untracked yet files in **working directory**.

## Rinse and repeat
So, now **Git** tracks `new_file` file. If we will edit this file to have new information in it and do another `git status`, we will see this
```
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   new_file

no changes added to commit (use "git add" and/or "git commit -a")
```

It means that in our **staging area** there is nothing new that is ready to be commited, but since **Git** tracks our file, **Git** detected changes in the file (since the last **commit**), and it now *suggests* us to add those new changes, in order to create a new *snapshot* of a file

## Pushing to a remote repository
### Connecting SSH keys
