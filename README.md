# JUL 2024 PISCINE GIT WORKSHOP

# Table of Contents
- [What is Git?](#what-is-git)
    - [What is a Version Control System](#what-is-a-version-control-system)
- [What is a Repository?](#what-is-a-repository)
- [Tracking](#tracking)
- [Staging Area](#staging-area)
- [Commiting](#commiting)
- [Rinse and Repeat](#rinse-and-repeat)
- [Pushing to a Remote Repository](#pushing-to-a-remote-repository)
    - [Connecting SSH Keys](#connecting-ssh-keys)
    - [How to use Github](#how-to-use-github)
    - [How to connect the Local and Remote Repository](#how-to-connect-the-local-and-remote-repository)

# What is Git?
**Git** is a **Version Control System**. According to the creator of Git and what is written in Git's own repo's first commit
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

### What is a Version Control System?
A **Version Control System** is a **system** that **controls versions** of your project. So that, for example, if your project got a new feature, and it started to break something, it would be possible to go back to a stable version.

### Why use Git?
Git is very verbose. On each action Git usually gives a lot of information on what just happened, or if **Git** doesn't like something, it usually would output the problem description and potentially how to solve it.
Git also makes collaboration on projects easier through branches and merges.

## What is a Repository?
On a basic level, a **repository** is just a directory on a computer, that has `.git` subdirectory in it. `.git` directory is a storage of commits and other information that **Git** tracks.

There are two methods to create a repository:
- `init`ialise a repository in a directory
- `clone` an existing **remote** repository

Once you have your repository, you can start adding files to it.

## Tracking
One of the main things that **Git** does is tracking files, and changes in files. If you just `init`ialised a repository it won't have any files that **Git** would track, so when you add a file to your **working directory** and do `git status`, you will see a message like:
```
Untracked files:
    (use "git add <file>..." to include in what will be committed)
        new_file
```

In order to start tracking changes in a file, you will need to add it to the **staging area**, this is done using `git add <file>` command.

## Staging Area
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

## Rinse and Repeat
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

## Pushing to a Remote Repository
Now that we have some commits in our repository, we can push it to a **remote** repository, in order to do that, you need to have (or create) an account at a platform such as Github, Gitlab or any other that you like more. In order to set up a **remote** repository, follow these steps

### Connecting SSH Keys
If you are on a computer where you didn't generate an **SSH key** yet, start by creating an SSH key in your Terminal by typing `ssh-keygen`.\
After doing this *or* if you already did this on the campus computer, continue like this:
1. Go to your Home directory
2. Next go to your `.ssh` folder:
   - Show Hidden Files in the Settings at the top to find it (when using the File Explorer)
   - Type `cd .ssh/` (when using the Terminal)
3. Copy the contents of `id_rsa.pub` (Your **PUBLIC KEY**!)

Now that we have our public ssh key, we can move on to:
### How to use Github
1. Add your Public SSH Key to your Github:
    - https://github.com/settings/keys
    - Click on `New SSH key`
2. Create your first Repository:
   - Go to the *Your Repositories* page
   - Click on `New`
   - Chose a name, description (optional) and visibility of your repository
3. Now click on the `<> Code` Button and copy the SSH(!) key

### How to connect the Local and Remote Repository
For this, you have two options on what you can do:
- If you want to get a **local** copy of a **remote** repository, do `git clone <ssh key> <name>` in your Terminal to create a **local** repository that's immediately connected to the **remote** repository on Github
- If you want to connect an existing **local** repository to a **remote** repository, do `git remote add <name> <ssh key>` to connect it to the **remote** repository on Github

In case of the second option, you will get this message if you try to just `git push`:
```
fatal: No configured push destination.
Either specify the URL from the command-line or configure a remote repository using

    git remote add <name> <url>

and then push using the remote name

    git push <name>
```

By default, git doesn't know where to push changes from local repository, to push, we need to add information about which **remote** repository and branch we want to push to, by typing:
- `git push <name> <branch-name>`

And if you want to set a default *upstream*, so that git will know where to push in case if you write just `git push`, you can set it using following:
- `git push --set-upstream <name> <branch-name>`

Note that this *upstream* is set for each branch separately, so if you set it for `main` it doesn't mean that it will be able to `git push` from `dev` branch!

(If you are interested in more advanced options like **pushing to two remote repositories** or having **submodules**, check out [my quick guide](https://github.com/CottonKiwii/42_CommonCore/blob/main/How_To_Git_Gud.md)\
or [a longer tutorial by another 42 student](https://github.com/francisrafal/42-connect-multiple-remotes-tutorial)!)
