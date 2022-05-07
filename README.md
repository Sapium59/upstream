# upstream
**This repo records several experiments for exercising repository usage and management through command line. The repo expected to alter is `hello-world`.**

# Management actions list 
* Configure a local repository by cloning from a remote repo.
* Fetch (download) changed files from a rempte repo.
* Push local changes to GitHub.
* Merge / Synchronize: copy changes in `upstream` into `hello-world` while my local changes in `hello-world` should be remained. 
* Update local change to upstream (source) remote repo.

*This read-me file might be too long to read. I'm seeking for some acceptable solution.*

# Samples
## Basic Git knowledge:
* To change directory, type ``cd <path>``. Same as other terminals or bash shells.
* To show verbose log of the corresponding remote repo `hello-world`., type ``git remote -v``.
* For more grammar and usage, refer to https://docs.github.com/cn/get-started/using-git/about-git.
* Being local means on this machine. Being remote means on GitHub.
## Environment
**Local:** I have already created an empty directory called `repo` under local path `G:\\Git` for any further operation. Initial path is `G:/git/repo`.

**Remote:** Two relevent repos.
* A target repo `hello-world` at `https://github.com/zhu-yuefeng/hello-world`, containing nothing but a `readme.md` file at first. During the experiment a request to add another markdown file called `edit.md` will be pushed.
* A documentary repo `upstream` at `https://github.com/zhu-yuefeng/upstream`, containing a `readme.md` file which illustrates all experiment steps and expected results.

## Target: Configure local repo by cloning from remote repo.
Create local clone of `hello-world`, which would be operated by all means.
>
    git clone https://github.com/zhu-yuefeng/hello-world.git

>
    >
    Cloning into 'hello-world'...
    remote: Enumerating objects: 7, done.
    remote: Counting objects: 100% (7/7), done.
    remote: Compressing objects: 100% (5/5), done.
    remote: Total 7 (delta 1), reused 0 (delta 0), pack-reused 0
    Receiving objects: 100% (7/7), done.
    Resolving deltas: 100% (1/1), done.
    
Print information about `hello-world` in remote repository.
>
    cd hello-world
    git remote -v
>
    >
    origin  https://github.com/zhu-yuefeng/hello-world.git (fetch)
    origin  https://github.com/zhu-yuefeng/hello-world.git (push)

## Target: Fetch changed files from a rempte repo and merge it into local repo.
This should be done when remote repo is updated while local one is not. Fetch right after cloning makes no sense.
> 
    cd hello-world
    git remote -v
>
    >
    origin  https://github.com/zhu-yuefeng/hello-world.git (fetch)
    origin  https://github.com/zhu-yuefeng/hello-world.git (push)
Now we know there is a "fetchable" called `origin`. Let's fetch it from remote. 

*Note: A little change is made on remote so we have a repo from the local repo, making the fetch useful.
>
    git fetch origin
>    
    >
    remote: Enumerating objects: 1, done.
    remote: Counting objects: 100% (1/1), done.
    remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
    Unpacking objects: 100% (1/1), 620 bytes | 9.00 KiB/s, done.
    From https://github.com/zhu-yuefeng/hello-world
       6ff71bc..e36c97e  main       -> origin/main

Now we can merge the fetched repo to local repo.

Follow the grammar `git merge <remote_name>/<branch_name>`. Usually they are `origin` and `main` respectively.
>
    git merge origin/main
>
    >
    Updating c443b56..e36c97e
    Fast-forward

***Note: this whole target can be accomplished by simply `git pull <remote_name> <branch_name>`.

## Target: Make local changes and push to GitHub.
Create a new branch (line of development) to store any new changes. Then switch to it.
>
    git branch my-branch
    git checkout my-branch
>
    >
    Switched to branch 'my-branch'

Make changes, for example, create a file named `edit.md`under the same directory as `readme.md`. Stage the changed files through `git add <file_name>`.
Take a snapshot of the staging area (anything that's been added). `-m "my snapshot"` is a label to notify what is it.
>
    git add edit.md
    git commit -m "my snapshot"
>
    >
    [my-branch c443b56] my snapshot
     1 file changed, 2 insertions(+)
     create mode 100644 edit.md

Push changes to github.
>
    git push --set-upstream origin my-branch
>
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




