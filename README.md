# upstream

This repo acts as an upstream for a developer (myself) to exercise repository management in git.

Management actions include: 
* add this repo locally into origin repo,
* update local change to upstream (source) remote repo.


## sample

### bash code

    cd G:/git/repo/hello-world
    git remote add upstream https://github.com/zhu-yuefeng/upstream
    git remote -v

### expected output

    origin  https://github.com/zhu-yuefeng/hello-world (fetch)
    origin  https://github.com/zhu-yuefeng/hello-world (push)
    upstream        https://github.com/zhu-yuefeng/upstream (fetch)
    upstream        https://github.com/zhu-yuefeng/upstream (push)

