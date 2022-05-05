# upstream
**This repo acts as an upstream for exercising repository usage and management by command line.**

Management actions include: 
* Configure an origin repo, i.e. `hello-world`, as the repo that should be covered by `upstream`.
* Fork / Add `upstream` (as a fork) into origin repo (`hello-world`).
* Merge / Synchronize: copy changes in `upstream` into `hello-world` while my local changes in `hello-world` should be remained. 
* Update local change to upstream (source) remote repo.

*This read-me file might be too long to read. I'm seeking for some acceptable solution.*

# Samples
Several git abc:
* To change directory, type ``cd <path>``. Same as other terminals or bash shells.
* To get information about current repo, type ``git remote -v``.

## Target: Configure environment (here it is hello-world)
I create a directory called `repo` under path `G:\\git` for following operations:
* Change directory.
* Create local clone of my hello-world, which would be operated by all means.
* Change directory.
* Show current repo configureation.
### bash code
    cd G:/git/repo
    git clone https://github.com/zhu-yuefeng/hello-world
    cd G:/git/repo/hello-world
    git remote -v
### expected output
    origin  https://github.com/zhu-yuefeng/hello-world (fetch)
    origin  https://github.com/zhu-yuefeng/hello-world (push)

## Target: Configure a remote for a fork (here it is upstream)
* Configure `upstream` to fork, with grammar ``git remote add <local_name> <repo_url>``.
### bash code
    git remote add upstream https://github.com/zhu-yuefeng/upstream
    git remote -v
### expected output
    origin  https://github.com/zhu-yuefeng/hello-world (fetch)
    origin  https://github.com/zhu-yuefeng/hello-world (push)
    upstream        https://github.com/zhu-yuefeng/upstream (fetch)
    upstream        https://github.com/zhu-yuefeng/upstream (push)

## Target: Merge remote repo to loocal repo (**I didn't made it**)
