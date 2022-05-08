# upstream
**This repo shows how to manage interactions between a local repo and a remote repo though `GitBash`.**  
**The repo expected to be altered is `hello-world`.**

# Management interactions list 
* Clone: configure a local repository by cloning from a remote repo.  
* Pull: fetch changed files from a rempte repo and merge it into local repo.  
* Push: push local change to remote repo on GitHub.  

*In this file, bash inputs are written as code, while expected outputs are written as code beginning with a line of one `>`.*  
*This read-me file might be too long to read. I'm seeking for some acceptable solution.*

# Samples
## Basic Git knowledge:
* To change directory, type ``cd <path>``. Same as other terminals or bash shells.
* To show verbose log of the corresponding remote repo `hello-world`., type ``git remote -v``.
* For more grammar and usage, refer to https://docs.github.com/cn/get-started/using-git/about-git, or https://training.github.com/downloads/zh_CN/github-git-cheat-sheet/.
* Being **local** means on this machine. The `git init` operation works to create a local repo.  
Being **remote** means online on GitHub. It is updated only by `git push`.

## Environment
**Local:** I have already created an empty directory called `repo` under local path `G:\\Git` for any further operation. Initial path is `G:/git/repo`.  
**Remote:** Two remote repos.
* A target repo `hello-world` at `https://github.com/zhu-yuefeng/hello-world`, containing nothing but a `readme.md` file at first. During the experiment a request to add another markdown file called `edit.md` will be pushed.
* A documentary repo `upstream` at `https://github.com/zhu-yuefeng/upstream`, containing a `readme.md` file which illustrates all experiment steps and expected results.

## Clone: configure a local repository by cloning from a remote repo.
Create local clone of `hello-world`, which would be operated by all means.
```
git clone https://github.com/zhu-yuefeng/hello-world.git
```
```
>
Cloning into 'hello-world'...
remote: Enumerating objects: 7, done.
remote: Counting objects: 100% (7/7), done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 7 (delta 1), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (7/7), done.
Resolving deltas: 100% (1/1), done.
```

Print information about `hello-world` in remote repository.
```
cd hello-world
git remote -v
```
```
>
origin  https://github.com/zhu-yuefeng/hello-world.git (fetch)
origin  https://github.com/zhu-yuefeng/hello-world.git (push)
```

## Pull: fetch changed files from a rempte repo and merge it into local repo).
This should be done when remote repo is updated while local one is not.
Fetching right after cloning makes no sense.  
Let's first check the remote repo. Remember we are under `G:/Git/repo/hello-world`.  
```
git remote -v
```
```
>
origin  https://github.com/zhu-yuefeng/hello-world.git (fetch)
origin  https://github.com/zhu-yuefeng/hello-world.git (push)
```

Now we know there is a "fetchable" called `origin`. Let's fetch it from remote.  
*Note: A little change is made on remote so we have a repo from the local repo, making the fetch useful.
```
git fetch origin
```
```
>
remote: Enumerating objects: 1, done.
remote: Counting objects: 100% (1/1), done.
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (1/1), 620 bytes | 9.00 KiB/s, done.
From https://github.com/zhu-yuefeng/hello-world
   6ff71bc..e36c97e  main       -> origin/main
```

Now we can merge the fetched repo to local repo.  
Follow the grammar `git merge <remote_name>/<branch_name>`. Usually they are `origin` and `main` respectively.
```
git merge origin/main
```
```
>
Updating c443b56..e36c97e
Fast-forward
```

***Note: this whole target can be accomplished by following code:***
```
git pull <remote_name> <branch_name>
```

## Push: push local change to remote repo on GitHub.
Create a new branch (line of development) to store any new changes. Then switch to it.
>
git branch my-branch
git checkout my-branch
>
>
Switched to branch 'my-branch'

Then we make some changes, for example, create a file named `edit.md` under the same directory as `readme.md`. Stage the changed files through `git add <file_name>`.
Take a snapshot of the staging area (anything that's been added). `-m "my snapshot"` is a label to notify what is it.
```
git add edit.md
git commit -m "my snapshot"
```
```
>
[my-branch c443b56] my snapshot
 1 file changed, 2 insertions(+)
 create mode 100644 edit.md
```

Push changes to GitHub.
```
git push --set-upstream origin my-branch
```
```
>
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 285 bytes | 285.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote:
remote: Create a pull request for 'my-branch' on GitHub by visiting:
remote:      https://github.com/zhu-yuefeng/hello-world/pull/new/my-branch
remote:
To https://github.com/zhu-yuefeng/hello-world.git
 * [new branch]      my-branch -> my-branch
branch 'my-branch' set up to track 'origin/my-branch'.
```



