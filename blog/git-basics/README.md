# Git basics

## What is Git?

### What is a version control system?

Let's say you are a beginning developer. While you are working on your code, you perhaps are going to make some "backup" files, so that you can recheck, how the code looked like before you changed it.
Problems with that are:

* you perhaps cannot find directly, where the code has changed
* you don't know anymore which "backup" file is the last one
* you have dozens of backup files you probably don't need anymore

Now let's say, you are working together with another developer. If it is only one more developer it is probably still easy enough to communicate, in which file you are working at the moment. But if you build up a team of - let's say 4 developers - it is getting already a lot more complicated.
These problems can be solved with version control systems.

A typical feature list of a VCS:

* **versioned files:** you cannot overwrite anything really - everytime you commit, you make a new version inside of the VCS
* **diff:** you can see directly, where changes were made and when they were made
* **multiuser:** you can work within a team without always screaming at your team members, in which file you want to work - just do it, and they or you can merge the differences later

Git is a version control system. While there are other VCS which are tracking the folder layout, Git tracks the file contents.

## Git installation

### Linux

Get Git via your terminal:

```bash
sudo apt-get install git
```

Done.

### Other platforms

* [Install Git on Windows](https://confluence.atlassian.com/display/BITBUCKET/Set+up+Git+and+Mercurial)
* [Install Git on Mac/OsX](https://confluence.atlassian.com/pages/viewpage.action?pageId=269981802)

## First steps with Git into a happier coder live

To check your installation (I expect you installed a command line tool, for following this howto) start your console and type:

```bash
git
```

and hit enter.

If your installation was successful, you get now a list of git commands.

### Initialize a Git repository

Now go into your preferred project folder - for example /opt/projects and create a new folder called "testing".

```bash
cd /opt/projects
mkdir testing
```

Get into that folder and initialize now your first Git repository.

```bash
cd testing
git init
```

That's it - your first Git repository is ready to use.

### Configure Git user

Configure your username and email address and put in for example your github credentials:

```bash
git config --global user.name myGitUsername
git config --global user.email myEmailAddress@example.com
```

The `--global` makes these configuration variables system-wide.

### Getting your first file into the Git repository

So - now put a file into the folder we created in the step above called README.md and put some text in it. Then let's see, what git is doing.

```bash
git status
```

Now you should see the filename you created before. To get this file into your local repository, you have to say, that you want to have it in your next commit with:

```bash
git add README.md
```

Now let git show you the status again and it will tell you that it has the README.md prepared for the commit. To finally really get it in the repository make:

```bash
git commit -m "initial commit with README.md"
```

If you let git show you the status again, it will tell you that there are no more changes to commit.

### Remote Repositories

Now we are going to use a remote repository with wich it would be possible to work in a team. So first of all we need a new repository. So go out of your current project directory, make a new folder and initialize there a new git repository with the bare flag:

```bash
cd ..
mkdir myBareRepo
cd myBareRepo
git init --bare
```

This repository will not show later the files you commit in the normal directory structure. After initializing it you won't work directly on this repository. Instead of that you will push your contents to it or pull from it.

Go again one directory up and clone the bare repository with:

```bash
git clone /opt/projects/myBareRepo myLocalRepo
```

If everything went fine, you have now a new folder called myLocalRepo.

Go into your new folder and add a testme.txt with random contents. Add and commit that file to your local repository like shown above.

Now let's see what our git clone did and let's ask git, which remotes our repository has:

```bash
git remote -v
```

The `-v` stands for verbose and tells git to also show us the paths of the remote repositories. So there we see our bare repository. To get our commits of the local repository into the bare ones, we have to:

```bash
git push -u origin master
```

The `-u` stands for "set upstream"

> For every branch that is up to date or successfully pushed, add upstream (tracking) reference, used by argument-less git-pull(1) and other commands.  
> [from git-scm.com/docs/git-push](http://git-scm.com/docs/git-push)

To show you know how to pull - go back into the testing folder. There we add our bare repository to the remotes and pull from it.

```bash
cd ../testing
git remote add origin /opt/projects/myBareRepo
git pull origin master
```

Now you have the README.md and the testing.txt in your project directory.

## What you should not commit

There are some type of files, which you should not commit into your repository:

* temporary files - for example from IDEs
* generated files - for example builded C++ executeables or minified JavaScript/CSS versions
* IDE project files - for example Visual Studio project files

## Conclusion

You know now the main commands for git. There are more that you will have to know when working in a team, but for now it should be enough to start working with git.
