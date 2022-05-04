# Github入门笔记-PartB
@(读书笔记组)[GitHub, GitHub 101, GitHub 漫游指南, Git工作流程, Github入门笔记]

[toc]



* [Github入门笔记\-PartB](#github入门笔记-partb)
  * [7\.  完整命令参考](#7--完整命令参考)
    * [Pull request on Github](#pull-request-on-github)
  * [8\. 从远程仓库获取](#8-从远程仓库获取)
    * [8\.1 git clone——获取远程仓库](#81-git-clone获取远程仓库)
    * [8\.2 git pull \-\- 获取最新的远程仓库分支](#82-git-pull----获取最新的远程仓库分支)
  * [9\. Github日常操作遇到问题记录](#9-github日常操作遇到问题记录)
    * [9\.1 Git Clone之后提示无仓库信息](#91-git-clone之后提示无仓库信息)
    * [9\.2 为什么做了大量代码调整，Github上却只有一个commit?](#92-为什么做了大量代码调整github上却只有一个commit)
    * [9\.3  What is the difference between 'git pull' and 'git fetch'?](#93--what-is-the-difference-between-git-pull-and-git-fetch)
    * [9\.4 fatal: The current branch xxx has no upstream branch\.](#94-fatal-the-current-branch-xxx-has-no-upstream-branch)
    * [9\.5 Permission to xxx \.git denied to VarianWrynn\.](#95-permission-to-xxx-git-denied-to-varianwrynn)
    * [9\.6 remote origin already exists\. （<a href="https://www\.datree\.io/resources/git\-error\-fatal\-remote\-origin\-already\-exists" rel="nofollow">git remote set\-url</a> 解决）](#96-remote-origin-already-exists-git-remote-set-url-解决)
    * [9\.7 Github上图床不能显示的问题](#97-github上图床不能显示的问题)
      * [为什么命名为etc？](#为什么命名为etc)
  * [10\. 参考链接](#10-参考链接)
  * [11\. 文档修订记录](#11-文档修订记录)



这篇是[Github入门笔记](https://www.evernote.com/l/ALrece8X4B9MzIkmhiQfbxOcBBD3Zt-sM7U/)的第二部分，原先的文章章节太长导致马克飞象和Evernote之间的同步比较慢，所以拆分成两篇。


![@||520x0](./1616410781546.png)


## 7.  完整命令参考
每一次创建一个新仓库都要翻阅手册好久，有点浪费时间，说明对整个流程还不熟悉，特此记录下来：

1. 在github原创仓库创建一个仓库比如叫`SSMiniProgram-BG`

2. 首先在`D:/Lee/`目录下创建 `SSMiniProgram-BG` 文件夹（与远程仓库同名），执行初始化命令：

```
cd SSMiniProgram-BG/
$ git init
Initialized empty Git repository in D:/Lee/SSMiniProgram-BG/.git/
```

3. 使用branch和status命令查看状态：

```
$ git branch
$ git status
On branch master
No commits yet
nothing to commit (create/copy files and use "git add" to track)
```

4.  使用`git remote add orgin`命令讲本地的仓库与原创的仓库链接起来：

```
$ git remote add origin git@github.com:VarianWrynn/SSMiniProgram-BG.git
```

5.  在本地仓库添加一些文件，然后使用`add`, `commite`命令提交到本地缓存区
```
$ git add .
$ git commote -m "Lee"
$ git commit -m "Lee"
[master (root-commit) 62a9ee9] Lee
 1 file changed, 65 insertions(+)
 create mode 100644 README.md
```

7. 使用`git push -u origin master`推送到远程

```
$ git push -u origin master
Enter passphrase for key '/c/Users/leewo/.ssh/id_rsa':
```



### Pull request on Github

![Alt text](./1616053858888.png)

![Alt text](./1616053919862.png)

![Alt text](./1616054020104.png)



## 8. 从远程仓库获取

### 8.1 git clone——获取远程仓库

在本地新建一个文件夹，用于存储即将从远程克隆下来的数据，然后打开`git bash`切到该目录下，使用如下命令：

```
$ git clone git@github.com:VarianWrynn/Tutorial.git
```

- **Git clone 项目到[本地指定目录](http://www.xiaoshu168.com/linux/294.html)**

```
git -c diff.mnemonicprefix=false -c core.quotepath=false clone --recursive https://git.coding.net/gamedaybyday/HelloGit.git D:\Git\HelloGit
```

简单写法：

```
git clone https://git.coding.net/gamedaybyday/HelloGit.git D:\Git\HelloGit
```

以上这种写法我在2020-12-14测试无效（可能Mac机器下有效），在Windows下必须先切换到指定的folder下再使用`git clone`命令拉取：

![@||550x0](./1607934485459.png)


### 8.2 git pull -- 获取最新的远程仓库分支

```
Lenovo@DESKTOP-PBJEFFJ MINGW64 /f/Lee/Githubs/ShiningStarsMiniProgram (master)
$ git pull origin master

---------------------
remote: Enumerating objects: 18, done.
remote: Counting objects: 100% (14/14), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 8 (delta 5), reused 6 (delta 4), pack-reused 0
Unpacking objects: 100% (8/8), 1.47 KiB | 4.00 KiB/s, done.
From github.com:VarianWrynn/ShiningStarsMiniProgram
 * branch            master     -> FETCH_HEAD
   f689f45..f2bdd53  master     -> origin/master
Updating f689f45..f2bdd53
Fast-forward
 components/classic/music/index.js | 12 ++++++++++++
 1 file changed, 12 insertions(+)

```

如果没有加上后面的`orgin master`参数，似乎会报错：
```
Lenovo@DESKTOP-PBJEFFJ MINGW64 /f/Github/ShiningStarsMiniProgram (master)
$ git pull
Connection reset by 140.82.112.4 port 22
fatal: Could not read from remote repository.

Please make sure you have the correct access rightsl
and the repository exists.
```



## 9. Github日常操作遇到问题记录

### 9.1 Git Clone之后提示无仓库信息

今天在公司的机器从Github上使用`git clone`获取一个仓库下来，提示获取成功 :

```
Lenovo@DESKTOP-PBJEFFJ MINGW64 /f/Github/ShiningStarsMiniProgram
$ git clone git@github.com:VarianWrynn/ShiningStarsMiniProgram.git

----------------------

Cloning into 'ShiningStarsMiniProgram'...
Warning: Permanently added the RSA host key for IP address '140.82.112.4' to the list of known hosts.
remote: Enumerating objects: 312, done.
remote: Counting objects: 100% (312/312), done.
remote: Compressing objects: 100% (189/189), done.
Receiving oremote: Total 312 (delta 85), reused 285 (delta 63), pack-reused 0
Receiving objects: 100% (312/312), 1.39 MiB | 663.00 KiB/s, done.
Resolving deltas: 100% (85/85), done.
```

**但是使用常见命令查询报错：**

```
Lenovo@DESKTOP-PBJEFFJ MINGW64 /f/Github/ShiningStarsMiniProgram
$ git status
fatal: not a git repository (or any of the parent directories): .git

Lenovo@DESKTOP-PBJEFFJ MINGW64 /f/Github/ShiningStarsMiniProgram
$ git branch
fatal: not a git repository (or any of the parent directories): .git
```

然后去Stackoverflow查看，还真遇到相同的问题：
[《“fatal: Not a git repository (or any of the parent directories)” from git status》](%E2%80%9Cfatal:%20Not%20a%20git%20repository%20%28or%20any%20of%20the%20parent%20directories%29%E2%80%9D%20from%20git%20status)

**You have to actually cd into the directory first**:

```
$ git clone git://cfdem.git.sourceforge.net/gitroot/cfdem/liggghts
Cloning into 'liggghts'...
remote: Counting objects: 3005, done.
remote: Compressing objects: 100% (2141/2141), done.
remote: Total 3005 (delta 1052), reused 2714 (delta 827)
Receiving objects: 100% (3005/3005), 23.80 MiB | 2.22 MiB/s, done.
Resolving deltas: 100% (1052/1052), done.

$ git status
fatal: Not a git repository (or any of the parent directories): .git
$ cd liggghts/
$ git status
# On branch master
nothing to commit (working directory clean)
```

按照Stackoverflow上操作，问题解决：

```
$ git clone git://cfdem.git.sourceforge.net/gitroot/cfdem/liggghts
Lenovo@DESKTOP-PBJEFFJ MINGW64 /f/Github
$ cd ShiningStarsMiniProgram/

Lenovo@DESKTOP-PBJEFFJ MINGW64 /f/Github/ShiningStarsMiniProgram (master)
$ git branch
* master
```

### 9.2 为什么做了大量代码调整，Github上却只有一个commit?

今天对后端新增了一张表，做了大量的[代码调整](https://github.com/VarianWrynn/SSMiniProgram-BG/commit/13da36e3c0c8fc6623129b0ecf22fc7f57a3313e)。



但是只算一个[commit](https://github.com/VarianWrynn/SSMiniProgram-BG/commits/master):

![@||360x0](./1613741578374.png)

![@删除了6万8千个地方](./1615364091942.png)








而且页面上点亮的那个方格很暗淡：

![@||200x0](./1613741590473.png)






这说明：
- 代码需要经常Commit，或者Push（待测试）到Server才可以快速点亮。

### 9.3  What is the difference between 'git pull' and 'git fetch'?
![Alt text](./1615184393620.png)















**In the simplest terms, `git pull` does a `git fetch` followed by a `git merge`.**

You can do a `git fetch` at any time to update your remote-tracking branches under `refs/remotes/<remote>/`.

This operation never changes any of your own local branches under `refs/heads`, and is safe to do without changing your working copy. I have even heard of people running `git fetch` periodically in a cron job in the background (although I wouldn't recommend doing this).

A `git pull` is what you would do to bring a local branch up-to-date with its remote version, while also updating your other remote-tracking branches.

From the Git documentation for [**git pull**](http://git-scm.com/docs/git-pull):

> In its default mode, `git pull` is shorthand for `git fetch` followed by `git merge FETCH_HEAD`.

1. [What is the difference between 'git pull' and 'git fetch'? --Stackoverflow](https://stackoverflow.com/questions/292357/what-is-the-difference-between-git-pull-and-git-fetch?rq=1)
2. [从程序员枪杀案谈git push -f](http://www.mzh.ren/git-push-force.html)

### 9.4 fatal: The current branch xxx has no upstream branch.

```
$ git push
fatal: The current branch Branch-20210221 has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin Branch-20210221
```

原因： 当前分支主服务器（Github）没有上游分支，推送当前分支并将远程服务器设置为上游。

解决：

```
$ git push -set-upstream origin Branch-20210221
error: did you mean `--set-upstream` (with two dashes)?
```
可以看到Gituhub越来越智能，还会提醒我是不是少了一个dashe.

```
$ git push --set-upstream origin Branch-20210221
Enter passphrase for key '/c/Users/leewo/.ssh/id_rsa':
```
**以上命令也可以支持Tab自动补全**（比如我输入 git push --s + tab, 则客户端自动帮我补全--set-upstream）

### 9.5 Permission to xxx .git denied to VarianWrynn.

```vim
$ git push
Enter passphrase for key '/c/Users/lee.wang/.ssh/id_rsa':
ERROR: Permission to shimohq/chinese-programmer-wrong-pronunciation.git denied o VarianWrynn.
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```

背景： 我本地直接从Github上Clone一个别人的项目修改完直接push上去提示报错。

[In this case what](https://stackoverflow.com/questions/39147285/git-push-permission-denied-to-user-could-not-read-from-remote-repository) you can do is

1. Fork this project to your account;
2. Make your commits;
3. Push to your repository;
4. Submit a merge request to the original project;

This way you can continue your work on your forked repository or contribute to the original project (always good to return something good to the community).



###  9.6 remote origin already exists. （[git remote set-url](https://www.datree.io/resources/git-error-fatal-remote-origin-already-exists) 解决）

```
$ git remote add origin git@github.com:VarianWrynn/chinese-programmer-wrong-pronunciation.git
fatal: remote origin already exists.
```

通过阅读这篇《[Git error - Fatal: remote origin already exists and how to fix it](https://www.datree.io/resources/git-error-fatal-remote-origin-already-exists)》问题得到解决：

```
$ git remote set-url origin git@github.com:VarianWrynn/chinese-programmer-wrong-pronunciation.git
```

可以看到本地比远程的代码更新，Gitbash客户端提示需要Push

```
$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```


```
$ git push
Enter passphrase for key '/c/Users/lee.wang/.ssh/id_rsa':
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 462 bytes | 231.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:VarianWrynn/chinese-programmer-wrong-pronunciation.git
   4619dd7..0de20b4  master -> master
```



### 9.7 Github上图床不能显示的问题

在新建了一个WOW[中文对照](https://github.com/VarianWrynn/WOWEnglishName)的Markdown项目的时候，遇到图床一直展示不出来，不论怎么尝试重新上传都不行。

<img src="./1616390507557.png" alt="@||790x0" style="zoom:67%;" /> 

在Google上检索了很久都没有结果（后来才知道国外基本不会遇到这种问题）。最后在中文世界找到了解决方法。


1. **C:\Windows\System32\drivers\etc\hosts 进入hosts**文件
2. 在hosts文件文件最后面加入如下代码：

```vbscript
# GitHub Start 
192.30.253.112    github.com 
192.30.253.119    gist.github.com
151.101.184.133    assets-cdn.github.com
151.101.184.133    raw.githubusercontent.com
151.101.184.133    gist.githubusercontent.com
151.101.184.133    cloud.githubusercontent.com
151.101.184.133    camo.githubusercontent.com
151.101.184.133    avatars0.githubusercontent.com
151.101.184.133    avatars1.githubusercontent.com
151.101.184.133    avatars2.githubusercontent.com
151.101.184.133    avatars3.githubusercontent.com
151.101.184.133    avatars4.githubusercontent.com
151.101.184.133    avatars5.githubusercontent.com
151.101.184.133    avatars6.githubusercontent.com
151.101.184.133    avatars7.githubusercontent.com
151.101.184.133    avatars8.githubusercontent.com
 
 # GitHub End
```
3. 重新打开之前的.md文件即可显示图片

<img src="./1616390553308.png" alt="Alt text" style="zoom: 50%;" />   





#### 为什么命名为etc？

早期UNIX中，贝尔实验室的解释是：`etcetra directory` 。 etc. 就是Et cetra。表示其他、等等什么的，英语里能常常看都这个缩写的。是用来放其他不能归类到其他目录中的内容。

后来FHS规定用来放配置文件，就解释为："**`Editable Text Configuration`**" 或者 "**`Extended Tool Chest`**"。



### 9.8 [How do I make a Git commit in the past?](https://stackoverflow.com/questions/3895453/how-do-i-make-a-git-commit-in-the-past)

```vbscript
git commit --date="10 day ago" -m "Your commit message" 
```

<img src="./image-20220505221246794.png" alt="image-20220505221246794" style="zoom:80%;" /> 



```asciiarmor
git commit --date=1649504560 -m 'xxx'
```



甚至还提供了一个专门的工具地址：https://github.com/OBKoro1/autoCommit



## 10. 参考链接

1. [Github入门笔记-PartA](https://www.evernote.com/l/ALrece8X4B9MzIkmhiQfbxOcBBD3Zt-sM7U/)
2. [Github入门笔记-PartB](https://www.evernote.com/l/ALo59sgLmrdD_JgeV8NsMqJpISPYL_u72cY/)
3. 《Github入门与实践》
4. . [阮一峰：Git 使用规范流程](https://www.techug.com/post/git-use-process.html)
5. . [阮一峰：Git 使用规范流程](https://www.ruanyifeng.com/blog/2015/08/git-use-process.html)
6. . [如何撤销 Git 操作？- 阮一峰的博客](http://www.ruanyifeng.com/blog/2019/12/git-undo.html)
7. [Git 工作流程-阮一峰的博客](http://www.ruanyifeng.com/blog/2015/12/git-workflow.html)
8. [GitHub Actions 入门教程-阮一峰的博客](http://www.ruanyifeng.com/blog/2019/09/getting-started-with-github-actions.html)
9. [3.6 Git 分支 - 变基(rebase)](https://git-scm.com/book/zh/v2/Git-%E5%88%86%E6%94%AF-%E5%8F%98%E5%9F%BA)
10.  [Git Basics - Recording Changes to the Repository -- git-scm](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository)
11.  [Git 原理入门 -- 阮一峰的博客](http://www.ruanyifeng.com/blog/2018/10/git-internals.html)
12.   [Understanding the GitHub flow -- Github Guides](https://guides.github.com/introduction/flow/)
13.  [Getting Started with GitHub Pages -- Github Guides](https://guides.github.com/features/pages/)
14.   [Things About Git and Github You Need to Know as Developer --Medium](https://medium.com/swlh/things-about-git-and-github-you-need-to-know-as-developer-907baa0bed79)
15.  [改变世界的一次代码提交（Git 第一次提交的源代码分析及带来的启示）](https://hutusi.com/articles/the-greatest-git-commit)
16.  [【精华】git remote set-url](https://www.datree.io/resources/git-error-fatal-remote-origin-already-exists)
17.  [github中加入图片方法、以及解决图片不能正常显示的问题 --csdn](https://blog.csdn.net/qq_45700583/article/details/108814562)
18.  [【最新】解决Github网页上图片显示失败的问题](https://blog.csdn.net/qq_38232598/article/details/91346392)
19.  [enter link description here](https://www.bilibili.com/video/BV1tf4y1e7yt?p=6&spm_id_from=pageDriver)



## 11. 文档修订记录

| 版本号|     变化状态|   简要说明|  日期	|   参与者   |
| :-------- | :--------| :------ |:------ |:------ |
| V0.1|   建立| 文档初建|2020-3-1| Lee|
|V0.2|增加| 新增`全局初始配置`章节| 2020-3-3|Lee|
|V0.3|增加| 增加`SSH Key设置`章节|2020-3-4|Lee<br>邹小青|
|V0.4|增加|增加`牛刀小试`章节|2020-3-12|Lee|
|V0.5|增加|增加`5.3 SSH可能并不校验邮箱`|2020-3-12|Lee|
|V0.6|增加|新增描述`将本地仓库推送到远程仓库`的章节描述|2020-3-15|Lee|
|V0.7|增加|添加参考链接|2020-3-23|Lee|
|V0.8|修改|为了同步方便讲一篇文章拆分为两个部分|2020-3-26|Lee|
|V0.9|增加|增加了`git clone`之后没有仓库的报错记录|2020-3-30|Lee|
|V0.10|增加|添加了一些有趣有用的文章链接|2020-10-10|Lee|
|V1.0|增加|根据3月份记录的操作文档，重新操作了一次流程;<br>添加记录如何Clone git到指定目录|2020-12-14|Lee|
|V1.0|增加|新增描述如何尽可能多点亮页面的contributions | 2021-2-19|Lee|
|V1.1|增加|新增fatal: The current branch xxx has no upstream branch.|2021-2-21|Lee|
|v1.2|增加|调整文章结构，新增最近操作过程中遇到的问题记录|2021-3-21|Lee|

*变化状态：建立，修改，增加，删除









