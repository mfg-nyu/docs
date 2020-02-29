# Using Git and GitHub

Git is a widely-used tool to facilitate collaboration in coding projects. While
Git can be totally run offline, we host our coding projects on GitHub, so 
members can contribute to them. 

This tutorial is meant to be a useful reference for frequent git commands.
For a full reference, check out git's man page.

- [Using Git and GitHub](#using-git-and-github)
  - [Getting started](#getting-started)
  - [Getting a local copy of a project](#getting-a-local-copy-of-a-project)
  - [Create a new branch](#create-a-new-branch)
  - [Switching branches](#switching-branches)
  - [Writing your own commit](#writing-your-own-commit)
  - [Synchronizing (pushing) to GitHub](#synchronizing-pushing-to-github)

## Getting started

- [How to install on Windows, macOS, and Linux](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [Excellent tutorial by Corey Schafer (~30 min)](https://www.youtube.com/watch?v=HVsySz-h9r4&t=882s)

**Very useful resources**

- [Commit message best practices (from Erlang)](https://github.com/erlang/otp/wiki/writing-good-commit-messages)
  - To summarize:
    - Title line: less than 50 characters, doesn't end with a period
    - Description (optional): each line less than 72 characters
- [Guide on Git from GitHub](https://guides.github.com/introduction/git-handbook/)
- [Visualizing Git (as nodes and link lists)](http://git-school.github.io/visualizing-git/)
- [Video of Linus Torvalds, creator of Linux and Git, talking Git stuff (~70min)](https://www.youtube.com/watch?v=4XpnKHJAok8)

## Getting a local copy of a project

```
git clone <PROJECT_URL>  // find the url in the repo's 'clone or download' button
cd <DIRECTORY_NAME>
```

## Create a new branch

After cloning a repository to your computer, you should be on the master 
branch (usually, you could see your branch next to your current directory name).
It's a good idea to make changes (commit) in a new branch, only merging to 
master when the changes are well tested.

To create a new branch, do

```
git checkout -b <BRANCH_NAME>   // -b stands for build
```

## Switching branches

To switch to another existing branch, do

```
git checkout <BRANCH_NAME>
```

Checking out to an non-existent branch is not allowed. To distinguish checking
out to new branches, we have the aforementioned `-b` flag.

## Writing your own commit

Commits are timestamped snapshots of a project. To create a commit that would
store all the changes you've made since the previous commit, do:

```
git add .   // run this from the root directory of the project
git commit -m "<within the quotes, write your commit message>"
```

Often, it's a good idea to cherry-pick changes you've made when writing a 
commit, rather than committing everything at once. This is because the changes 
being made could relate to various functionalities: for instance, when creating 
an API, one would frequently write the code for accessing the database, endpoint
setup, url routing, and input data validation together. It would be a good idea 
to split these changes into several commits, each focusing on one issue, rather 
than one big commit. Small commits can help us "replay" changes in the project 
in greater granularity.

Picking out the changes you want to commit (or "staging", in git parlance), 
can be done in a code editor like VSCode or in command line. See how to 
selectively stage in VSCode by searching "Stage selected" in
[this tutorial](https://code.visualstudio.com/docs/getstarted/tips-and-tricks).

Alternatively, in command line, using

```
git add -p
```

would give you the ability to selectively add the changes you want to commit
to the staging area. After doing so, you can continue committing by 
`git commit -m "<msg>"`.

***Strive for small commits, each focusing on one specific issue.***

## Synchronizing (pushing) to GitHub

Note that your commit remains local after you finish the commit command.
For these changes to be reflected in GitHub, do

```
// first time pushing commit from a branch
git push --set-upstream origin <BRANCH_NAME>    

// going forward, this would be sufficient
git push
```
