# 一、Git管理修改文件
1. Git管理修改，当使用git add，命令后，在工作区的第一次修改会被放入暂存区，准备提交，但是若在工作区做了第二次修改而没有放入暂存区时，git commit只会把放入暂存区的第一次修改提交，第二次不会被提交。

2. 提交后，使用以下命令查看工作区和版本库里面最新版本的区别：
```
$ git diff HEAD -- test.txt
```
3. 使用以下命令查看工作区和暂存区的区别
```
$ git diff -- test.txt
```
4. 使用以下命令可丢弃工作区的修改，但不会丢弃添加到暂存区的修改：
```
$ git checkout -- test.txt
```
5. 若已add了修改，利用以下命令可将暂存区的修改回退到工作区，即回到修改文件且未add的状态：
```
$ git reset HEAD test.txt
```

# 二、删除文件
1. 若在工作区新建了另一个文件temp.txt，现要删除该文件：
```
$ rm temp.txt
```
2. 此时Git知道我删除了文件temp.txt，因此工作区和版本库就不一致了，使用git status可查看状态，若确实要从版本库中删除该文件，则用以下命令将文件从版本库中删除：
```
$ git rm temp.txt
$ git commit -m "remove temp.txt"
```

# 三、总结
```
//查看工作区和版本库里最新版本的区别
$ git diff HEAD -- test.txt

//查看工作区和暂存区的区别
$ git diff -- test.txt

//丢弃工作区的修改，不修改暂存区的修改，效果类似于修改了的文件还未add，丢弃这个修改使工作区和暂存区一致
$ git checkout -- test.txt

//将暂存区的修改回退成工作区的修改，效果类似于修改了文件并add了，则回退到修改还未add的状态
$git reset HEAD test.txt

//从版本库中删除文件
$ git rm temp.txt
$ git commit -m "commit message"
```
