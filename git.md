# Github commands
very good documentation on: https://www.atlassian.com/git/tutorials/

## create repo from folder:  
``` bash
git init
git add .
git commit -m "<commit message>"
# create repo online, then:  
git remote add origin <url>
git pull origin master --allow-unrelated-histories
git push -u origin master
``` 

## switch branch
Switching from master to "Areaplot". **Case-sensitive**!

``` bash
git checkout -b Areaplot
git branch --set-upstream-to=origin/Areaplot Areaplot
git fetch
git pull
```

## merging branches

1. prepare by switching to receiving branch
2. check for remote changes: fetch & pull
3. merge

``` bash
git checkout master
git fetch
git pull
git merge Areaplot
```