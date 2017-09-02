# 一、Git版本回退
1. 我们可对文件作多次修改和提交。在git中每次commit可被视为一次快照。如：对test.txt文件作以下修改：
版本1内容:
```
this is a test txt.
```
版本2内容：
```
this is a test txt.
add a line in my first change.
```
版本3内容：
```
this is a test txt.
add a line in my first change.
this is my third modify.
```

2. 使用下面的命令可查看每次修改：
```
$ git log
```
使用该命令我们可看到如下日志内容：
```
commit e130949a314a559b4f7ced1784598cb90785cc16
Author: yanjing01 <yanjing01@fangdd.com>
Date:   Sat Sep 2 17:17:59 2017 +0800

    third time to modify test.txt

commit 721e4ba1c4d03afc7bed7ed2dc9ee0d88607d785
Author: yanjing01 <yanjing01@fangdd.com>
Date:   Sat Sep 2 17:16:37 2017 +0800

    add second line in test.txt

commit 709a8a78d60f727180ed14b1084b1c36c8084ae5
Author: yanjing01 <yanjing01@fangdd.com>
Date:   Sat Sep 2 16:52:10 2017 +0800

    add content
```
从上面内容可看出每次对内容修改的提交记录，使用以下命令可简化输出内容：
```
$ git log --pretty=oneline
e130949a314a559b4f7ced1784598cb90785cc16 third time to modify test.txt
721e4ba1c4d03afc7bed7ed2dc9ee0d88607d785 add second line in test.txt
709a8a78d60f727180ed14b1084b1c36c8084ae5 add content
```
前面的一长串数字是commit的版本号id，Git必须知道当前版本是哪个版本。

3. Git用HEAD表示当前版本，HEAD^表示上个版本，HEAD^^表示上上个版本，HEAD~100表示上100个版本。为了回到上个版本，使用以下命令：
```
$ git reset --hard HEAD^
```
利用该命令可回到上一版本，但是使用git log查看版本库状态时发现之前的最新版本不见了。此时可利用最新版本的版本号回到这个版本：
```
$ git reset --hard e130949a314a559
```
版本号不必写全，git会自动匹配的。再用以下命令查看文件发现又回来了：
```
$ cat test.txt
```
Git版本回退速度很快，因为Git内部有一个指针指向当前版本的HEAD，当回退版本时Git只是简单的移动指针。所以我们让HEAD指向哪个版本号，就把当前版本定位在哪里。

4. 当我们回退到某个版本后，又想恢复到最新版本，但是找不到最新版本的commit id，可用以下命令找回之前的每一次命令记录：
```
$ git reflog
721e4ba HEAD@{0}: reset: moving to HEAD^
e130949 HEAD@{1}: commit: third time to modify test.txt
721e4ba HEAD@{2}: commit: add second line in test.txt
709a8a7 HEAD@{4}: commit: add content
```
发现执最新版本时的版本号是e130949，因此可利用该版本号恢复到最新版本：
```
$ git reset --hard e130949
```

# 二、总结
```
//查看版本控制系统历史记录
$ git log

//查看版本控制系统历史记录，每条记录只显示一行
$ git log --pretty=oneline

//版本回退
$ git reset --hard HEAD^
$ git reset --hard HEAD^^
$ git reset --hard HEAD~100

//根据版本号回退版本
$ git reset --hard e130949

//查看每次git命令和对应的版本号
$ git reflog
```


























