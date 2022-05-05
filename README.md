# upstream
**This repo acts as an upstream for exercising repository usage and management by command line. The repo expected to alter is `hello-world`.**

Management actions include: 
* Configure an origin repo.
* Fork / Add `upstream` (as a fork) into origin repo (`hello-world`).
* Merge / Synchronize: copy changes in `upstream` into `hello-world` while my local changes in `hello-world` should be remained. 
* Update local change to upstream (source) remote repo.

*This read-me file might be too long to read. I'm seeking for some acceptable solution.*

# Samples
## Grammar ABC:
* To change directory, type ``cd <path>``. Same as other terminals or bash shells.
* To show verbose log of the corresponding remote repo `hello-world`., type ``git remote -v``.
* More: refer to https://docs.github.com/cn/get-started/using-git/about-git

## Target: Configure local repo by cloning from reomte repo.
Being local means on this machine. 
Being remote means on GitHub.
I create a directory called `repo` under path `G:\\git` for any further operation.
### bash code
    cd G:/git/repo
    # Create local clone of `hello-world`, which would be operated by all means.
    git clone https://github.com/zhu-yuefeng/hello-world.git
### expected output
    Cloning into 'hello-world'...
    remote: Enumerating objects: 7, done.
    remote: Counting objects: 100% (7/7), done.
    remote: Compressing objects: 100% (5/5), done.
    remote: Total 7 (delta 1), reused 0 (delta 0), pack-reused 0
    Receiving objects: 100% (7/7), done.
    Resolving deltas: 100% (1/1), done.
### bash code
    cd hello-world
    git remote -v
### expected output
    origin  https://github.com/zhu-yuefeng/hello-world.git (fetch)
    origin  https://github.com/zhu-yuefeng/hello-world.git (push)

## Target: Make local changes and push to GitHub.
### bash code
    # create a new branch to store any new changes
    git branch my-branch

    # switch to that branch (line of development)
    git checkout my-branch

    # make changes, for example, create a file named `edit.md`under the same directory as `readme.md`.

    # stage the changed files
    git add edit.md

    # take a snapshot of the staging area (anything that's been added)
    git commit -m "my snapshot"

    # push changes to github
    git push --set-upstream origin my-branch
### expected output
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




