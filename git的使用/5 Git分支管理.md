# 一、Git分支管理
1. 在Git里主分支时master分支，HEAD严格来说不是指向提交，而是指向master，master才是指向提交的，所以HEAD指向的是当前分支。每次提交，master分支都会向前移动一步，指向最新的提交，随着不断的提交，master分支的线也会越来越长。

2. 当我们创建新的分支（如：dev）时，Git新建了一个指针交dev，指向master相同的提交，再把HEAD指向dev，就表示当前分支在dev上。从现在开始，对工作区的修改和提交就是针对dev分支的了。比如新提交一次后，dev指针往前移动一步，而master指针不变。

3. 假设我们在dev上的工作完成了，就可以把dev合并到master分支上。合并的最简单的方法是把master指向dev的当前提交来完成合并。合并完成之后，可以删除dev分支。删除dev分支就是把dev指针删掉，删掉后，我们就只剩下mastser分支了。

# 二、创建与合并分支
1. 利用下面的命令我们可以创建一个dev分支，并切换到dev分支上，参数-b表示创建并切换。
```
$ git checkout -b dev
```  
	
	该命令与下列命令等价：
	```
	$ git branch dev
	$ git checkout dev
	```

	可以用下面的命令查看当前分支，可以看出我们当前在dev分支上。
	```
	$ git branch
	* dev
	  master
	```

2. 现在在dev分支上可对文件进行修改和提交（add和commit），几条好之后切换回master分支：
```
$ git checkout master
```

3. 切换回master分支上查看被修改了的内容发现修改的内容不见了，这是因为那个提交在dev分支上，而master分支此时的提交没有任何变化，我们把dev分支的工作合并到master分支上，下面的git merge命令用于合并指定分支到当前分支。合并后，再查看原来文件的内容就可以看到最新内容了。
```
$ git merge dev
```

4. 合并完成后我们可以删除dev分支了，用下面的命令删除dev分支：
```
$ git branch -d dev
```

5. 有时候合并分支时会有冲突，我们可以用下面的命令查看分支的合并情况：
```
$ git log --graph --pretty=oneline --abbrev-commit
```

# 三、总结
```
//创建并切换到dev分支
$ git checkout -b dev

//创建dev分支
$ git branch dev

//查看所有分支
$ git branch

//切换到<branchname>分支
$ git checkout <branchname>

//将dev分支合并到master分支上
$ git merge dev

//删除dev分支
$ git branch -d dev

//用带参数的git log查看分支的合并情况
$ git log --graph --pretty=oneline --abbrev-commit
```





















