# Github commands
very good documentation on: https://www.atlassian.com/git/tutorials/

## Global

### setting your account's global identity:
``` bash
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```
### adding SSH-key to account:
https://help.github.com/en/articles/connecting-to-github-with-ssh

## Repositories

### submodules

#### clone git with submodules
`git clone --recursive https://github.com/sonydevworld/spresense.git`  
After repositories have been cloned, each submodule is in 'Detached HEAD' state. Master branch have to be checked out before you can start developing.  
`git submodule foreach git checkout master`

#### adding existing repo as submodule
https://git-scm.com/book/en/v2/Git-Tools-Submodules

use `git submodule add`:

``` bash
$ git submodule add https://github.com/chaconinc/DbConnector
Cloning into 'DbConnector'...
remote: Counting objects: 11, done.
remote: Compressing objects: 100% (10/10), done.
remote: Total 11 (delta 0), reused 11 (delta 0)
Unpacking objects: 100% (11/11), done.
Checking connectivity... done.
```



### create repo from folder:  
``` bash
git init
git add .
git commit -m "<commit message>"
# create repo online, then:  
git remote add origin <url>
git pull origin master --allow-unrelated-histories
git push -u origin master
``` 

### switch branch
Switching from master to "Areaplot". **Case-sensitive**!

``` bash
git checkout -b Areaplot
git branch --set-upstream-to=origin/Areaplot Areaplot
git fetch
git pull
```

### merging branches

1. prepare by switching to receiving branch
2. check for remote changes: fetch & pull
3. merge

``` bash
git checkout master
git fetch
git pull
git merge Areaplot
```
