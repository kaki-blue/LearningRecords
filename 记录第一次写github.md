# 记录第一次写github

##### 前情概要：以前在linux使用过github但已经忘光光了，并且上半年使用github绝大多数时间都是浏览别人的作业（orz），并没有发过任何互利互惠的信息，在程序设计与小组读论文进度更直观的双重push下，学习了一下如何简单操作github，并且再次记录以防电脑系统重装（最好不要）

#### 将本地电脑与个人网站连接起来

##### 0.0首先，下载一个执行程序

官网下载地址 [http://www.git-scm.com/download/]，一路next，亲测可用，然后将 bin 的路径加入系统变量的PATH里

##### 0.1打开Git Bash

是这种界面

![](https://github.com/halipai/MYIMAGES/raw/main/github0/0.png)

然后设置姓名和邮箱

```
git config --global user.name "yourname"
git config --global user.email "your@email.com"
```

git命令行中运行如下命令在.ssh文件夹中生成ssh key

```
ssh-keygen -t rsa -C "your@email.com"
```

然后一路回车就OK了

转到.ssh文件夹下，即在初始文件夹`C:\Users\用户名`下输入

```
cd .ssh
```

由于我初始时设置的使用vim格式，在.ssh文件夹下直接输入

```
vim config
```

在`config`文件中加入以下

```
Host github.com
  Hostname ssh.github.com
  User halipai
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/id_rsa
  Port 443
```

保存退出

##### 0.2在github加入ssh key

在.ssh文件夹下输入

```
vim id_rsa.pub
```

文件里是好长好长的字符串就是ssh key 如图

![](https://github.com/halipai/MYIMAGES/raw/main/github0/1.png)

然后在自己的github主页上，盗用一张别人的图片

![](https://github.com/halipai/MYIMAGES/raw/main/github0/2.png)

然后在git Bash中输入

```
ssh -T git@github.com
```

点一些`yes`，然后就会出现

![](https://github.com/halipai/MYIMAGES/raw/main/github0/3.png)

#### 1.如何提交java作业（fork别人代码并pull request）

##### 1.0 fork

点击这个fork，然后就可以在自己的主页里找到这个`Repository`

![](https://github.com/halipai/MYIMAGES/raw/main/github0/4.png)

##### 1.1更新fork

`题外话:这个功能对于提交java作业好像没有什么用途，因为pull request只看你的更新，不会覆盖从fork到提交过程中别人的更新`

在自己fork的代码的页面下

![](https://github.com/halipai/MYIMAGES/raw/main/github0/5.png)

网站默认是请求将自己的代码更新到源代码中，更改双方位置，然后点击`Create pull request`

![](https://github.com/halipai/MYIMAGES/raw/main/github0/6.png)

写一个严谨的标题，然后点击`Create pull request`

![](https://github.com/halipai/MYIMAGES/raw/main/github0/7.png)

然后继续同意（好多呐）

![](https://github.com/halipai/MYIMAGES/raw/main/github0/8.png)

![](https://github.com/halipai/MYIMAGES/raw/main/github0/9.png)

然后就可以看到

![](https://github.com/halipai/MYIMAGES/raw/main/github0/10.png)

这样就成功更新啦

##### 1.2下载代码到本地

如图，在自己fork的代码主页中，点击两下

![](https://github.com/halipai/MYIMAGES/raw/main/github0/11.png)

然后在git Bash中切换到要克隆到本地的文件夹，输入

```
git clone https://github.com/halipai/jwork-2021.git
```

（有时候网不好，要多试几次）

然后就可以在文件中修改啦，该加加该删删（ git方法比如branch，到现在也没会，爬爬爬）

##### 1.3将本地代码上传到自己的github上

在git Bash上将目录转到要上传的文件夹，然后输入

```
git add .
```

意思是将文件中代码从工作区添加到暂存区（不懂）

然后输入

```
git commit -m "firstcode"
```

“ ”中是注释

git commit 将暂存区里的改动给提交到本地的版本库

然后输入

```
git push
```

具体我也不懂蛤，反正github仓库就神奇地更新啦

##### 1.4提交代码（pull request）

与1.1相同，代码更新方向保持默认

##### 1.5 readme.md中的图片怎么办

第一次提交的readme.md中的图片竟然写了本地文件，有点尴尬

为了使第一次作业提交，直接把要提交的图片建了个Repository放到了自己的github上

建一个Repository，然后点击

![](https://github.com/halipai/MYIMAGES/raw/main/github0/12.png)

选择文件（夹），添加文件（夹）就可以快速加入图片了

##### 1.5 readme.md中github网站上的图片加载不出来怎么办
把`blob`改成`raw`就能正常显示了，妙极了
