# JUL 2024 Piscine Git Workshop

## Table of Contents
- [What is Git?](#what-is-git)
    - [What is a version control system](#what-is-a-version-control-system)
- [What is a repository](#what-is-a-repository)

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
