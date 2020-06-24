
# MISCall

* binwalk 查看文件格式，为gzip文件。解压两次

* .git 文件夹
``` 
// 查看日志
git log

// 查看stash了哪些存储
 git stash list
// 显示做了哪些改动，默认show第一个存储,如果要显示其他存贮，后面加stash@{$num}，比如第二个 git stash show stash@{1}
git stash show
// 应用某个存储,但不会把存储从存储列表中删除，默认使用第一个存储,即stash@{0}，如果要使用其他个，git stash apply stash@{$num} ， 比如第二个：git stash apply stash@{1} 
git stash apply
```

* python s.py