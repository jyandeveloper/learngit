# 一、Git远程仓库
1. 注册Giuhub账号，本地的Git仓库和Github仓库之间是通过SSH加密传输的，因此第一步先创建SSH Key。在用户住目录下，首先查看有没有.ssh目录，若有，则看该目录下有没有**id_rsa**和**id_rsa.pub**这两个文件，若已经有了可跳到下一步，没有则创建SSH Key：
```
$ ssh-keygen -t rsa -C "email@qq.com"
``` 

一路回车，不需要输入密码，最后成功在.ssh目录下生成id_rsa和id_rsa.pub两个文件，是SSH Key的密钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可放心地告诉他人。

2. 登陆Github账号，点击头像 -> Settings -> SSH and GPG keys -> New SSH Key，填写一个合适的Title（任意填写），在Key文本框中粘贴id_rsa.pub文件的内容，最后点击Add SSH Key就可以在Github上添加一个Key。

3. Github允许添加多个Key。假设我有若干台电脑，我可以用公司电脑提交，也可以用家里的电脑提交。只要把每台电脑的Key都添加到Github上，就可以在每台电脑上往Github上提交了。

# 二、添加远程库
现在，我已经在本地创建了Git仓库，我想在Github上创建一个Git库，且让这两个库进行远程同步。

1. 登陆Github后，在页面找到New repository，创建一个新仓库，在Repository name里填入一个适当的名字（如：learngit），其他设置保持默认值，点击Create repository，就可以成功创建一个新的Git远程仓库。创建好这个仓库后，此时仓库是空的，我们可以从这个仓库克隆出新的仓库，也可以把一个已有的本地仓库与之关联，然后把本地的内容push到Github仓库。</br>
2. 在本地learngit仓库下运行以下命令：
```
$ git remote add origin https://github.com/jyandeveloper/learngit.git
``` 
	
添加好之后，远程库的名字就是origin，这是Git的默认叫法，也可以改成别的，但是origin这个名字一看就知道是远程库。

3. 接着可以把本地库的所有内容push到远程库上，输入下面的命令，把当前master分支推送到远程。由于远程库是空的第一次push master分支时要加上-u参数，Git不但会把本地master分支的内容push到远程新的master分支上，还会把本地的master分支和远程的master分支关联起来，以后在push或pull时可简化命令。
```
$ git push -u origin master
```

推送成功后，Github远程仓库的内容就和本地仓库内容一致了。从现在起，本地提交可用下面的命令：</br>
```
$ git push origin master
```

# 三、从远程库克隆
1. 从远程库拉文件到本地可使用下面的命令：
```
$ git clone git@github.com:jyandeveloper/learngit.git
```

# 四、总结
```
//创建SSH Key
$ ssh-keygen -t rsa -C "email@qq.com"

//将本地库与远程仓库相关联
$ git remote add origin https://github.com/jyandeveloper/learngit.git

//提交本地文件到远程仓库
$ git push -u origin master
$ git push origin master

//拉取远程仓库文件到本地
git clone git@github.com:jyandeveloper/learngit.git
```
