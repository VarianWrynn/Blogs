# Github入门笔记-PartA
@(读书笔记组)[GitHub, GitHub 101, GitHub 漫游指南, Git工作流程, Github入门笔记]

[toc]





* [Github入门笔记\-PartA](#github入门笔记-parta)
  * [1\. 为什么Github受欢迎](#1-为什么github受欢迎)
  * [2\. <a href="https://www\.ruanyifeng\.com/blog/2015/08/git\-use\-process\.html" rel="nofollow">流程描述</a>](#2-流 程描述)
    * [2\.1 fork vs\. clone](#21-fork-vs-clone)
    * [2\.2 小青的解释](#22-小青的解释)
    * [2\.3 工作区/暂存区/仓库/远程仓库/快照](#23-工作区暂存区仓库远程仓库快照)
  * [3\. Developers化学反应\- Pull Request](#3-developers化学反应--pull-request)
    * [3\.1 Social Coding](#31-social-coding)
    * [3\.2 GitHub 最大的特征是“面向人”](#32-github-最大的特征是面向人)
  * [4\. 全局初始配置](#4-全局初始配置)
    * [4\.1 Git 安装](#41-git-安装)
      * [4\.1\.1  Mac](#411--mac)
      * [4\.1\.2 Windows](#412-windows)
    * [4\.2 设置姓名和邮箱地址](#42-设置姓名和邮箱地址)
    * [4\.3 提高命令输出的可读性](#43-提高命令输出的可读性)
    * [4\.4 通过命令行查看config全局配置](#44-通过命令行查看config全局配置)
  * [5\. 设置 SSH Key](#5-设置-ssh-key)
    * [5\.1 添加公开密钥](#51-添加公开密钥)
    * [5\.2 SSH通讯验证](#52-ssh通讯验证)
    * [5\.3 SSH可能并不校验邮箱](#53-ssh可能并不校验邮箱)
  * [6\. 牛刀小试](#6-牛刀小试)
    * [6\.1 Clone](#61-clone)
    * [6\.2 Submit](#62-submit)
    * [6\.3 push](#63-push)
  * [7\. 推送至远程仓库](#7-推送至远程仓库)
    * [7\.1 git remote add——添加远程仓库](#71-git-remote-add添加远程仓库)
    * [7\.2 git push——推送至远程仓库](#72-git-push推送至远程仓库)
    * [7\.3 推送至 master 以外的分支](#73-推送至-master-以外的分支)





--------------------------------

![@||400x0](./1583071818904.png)











> 图中只显示了一般的使用流程。实际上，所有仓库之间都可以进行 push 和 pull。即便不通过 GitHub，开发者 A 也可以直接向开发者 B 的仓库进行 push 或 pull。因此在使用前如果不事先制定规范，初学者往往会搞不清最新的源代码保存在哪里，导致开发失去控制。不过不用担心，只要各位随着本书的讲解亲自动手尝试，想掌握要领并不是一件难事。

## 1. 为什么Github受欢迎
在Github之前，developer一直都没有一个用来辅助多人协同编程的关键性软件。因此软件开发者们往往要将
- 版本管理系统
- BUG 跟踪系统
- 代码审查工具
- 邮件列表
- IRC 等

众多工具组合在一起，以实现多人协作。

## 2. [流程描述](https://www.ruanyifeng.com/blog/2015/08/git-use-process.html)

![@||560x0](./1584942993244.png)

















1. 在A的仓库中**`fork`**项目B （此时我们自己的github就有一个一模一样的仓库B，但是URL不同）
2. 将我们修改的代码**`push`**到自己github中的仓库B中
3. **`pull request`** ，主人(A)就会收到请求，并决定要不要接受你的代码。

要点：

**`fork`仅仅只是fork到你的github帐号上，你还需要用【`pull`】命令把代码拉回到你【本机的电脑】上。**

### 2.1 `fork` vs. `clone`

**`fork`**：在***github***页面，点击`fork`按钮。将别人的仓库复制一份到自己的仓库。

**`clone`**：将***github***中的仓库克隆到自己本地电脑中



通常来说 `clone` 来的仓库实际上与原仓库并没有任何关系。所以我们需要将原仓库设置为远程仓库，从该仓库获取（`fetch`）数据与本地仓库进行合并（`merge`），让本地仓库的源代码保持最新状态:

![@||480x0](./1592877521454.png)













> 摘自： 《***Github入门与实战***》  `6.5　仓库的维护`章节（作者：大塚弘记）。

### 2.2 小青的解释

- **PR流程**：
1. 在`Jira`创建**Story**类型事务，得到`AT-XXXX`
2. 拉取***master***最新代码

```
git clone https://github.com/edmodo/automodo.git
git checkout master #切换到master
git pull  #拉取master最新代码
```

3. 创建新的分支

```
git checkout -b AT-2903 #新建分支
```

4. 修改代码
5. 提交修改到暂存区

```
git status
git add<filename>
```

6. 提交代码到远程库

```
git diff #查看版本改动情况
git config --global user.name "xiaoqing"
git config --global user.emal zoe@example.com
git commit #将暂存区的改动提交到本地版本库
git push origin AT-29031 #提交本地库的修改到远程库
```

7. 登录github提交`branch AT-2903`的`Merge`请求

clone是把master复制到本地来 后面好基于`master`在本地`fork`分支。`push`是把本地修改好的分支 推送到远程去 相当于远程也有这个`fork` 分支 并包含你的修改。

- **fork**:

```vim
git checkout -b <branch_name>
```

###  2.3 工作区/暂存区/仓库/远程仓库/快照
![@||666x0](./1592472657652.png)






- `git clone`是把远程上整个仓库都拷贝到本地仓库上
- 因此远程仓库有多少个分支都会一起被拷贝下来
- 本地再使用git checkout命令把某个分支切到**工作区**；
- 而`git pull`可以直接从远程仓库拉去到**工作区**某个分支上；
> 2021-4-7 21:06:33

**[名词解释](http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)：**
| 名词      |     翻译 |   备注   |
| :-------- | --------:| :------: |
| Workspace |   工作区| |
|  Index / Stage|暂存区|| 
|**Repository**|仓库区（或本地仓库）| |
|**Remote**|远程仓库||
|**commit**|快照||

1. 需要通知 Git 哪些文件发生了变动。所有变动的文件，Git 都记录在一个区域，叫做"暂存区"（英文叫做 **`index`** 或者 **`stage`**）。通过`git add --all`来实现。
2. 暂存区保留本次变动的文件信息，等到修改了差不多了，就要把这些信息写入历史，这就相当于生成了当前项目的一个快照（**snapshot**）。
> 项目的历史就是由不同时点的快照构成。Git 可以将项目恢复到任意一个快照。快照在 Git 里面有一个专门名词，叫做 **`commit`**，生成快照又称为完成一次提交。
3. Git 提供了git commit命令，简化提交操作。保存进暂存区以后，只要git commit一个命令，就同时提交目录结构和说明，生成快照。
```
$ git commit -m "first commit"
```
4. `git checkout`命令用于切换到某个快照。
5. `index/stage`的[作用是允许roll-back](https://www.bilibili.com/video/BV1tf4y1e7yt?p=6&spm_id_from=pageDriver)一个提交。

![@||300x0](./1616411039289.png)











## 3. Developers化学反应- Pull Request

在 GitHub 这个聚集了世界各地软件开发者的地方，有个在过去绝对是无法想象的事正在飞速地进行着——素未谋面的开发者们隔着半个地球的距离共同开发软件。我们不妨称之为开发者之间的化学反应吧。这种事成为可能，都要归功于一个名为 Pull Request 的功能:

![@||600x0](./1583072623095.png)

Pull Request 是指开发者在本地对源代码进行更改后，向 GitHub 中托管的 Git 仓库请求合并的功能。开发者可以在 Pull Request 上通过评论交流，例如
- “修正了 BUG，可以合并一下吗？”
- “我试着做了这样一个新功能，可以合并一下吗？”等。

通过这个功能，开发者可以轻松更改源代码，并公开更改的细节，然后向仓库提交合并请求。而且，如果请求的更改与项目的初衷相违，也可以选择拒绝合并。

GitHub 的 Pull Request 不但能轻松查看源代码的前后差别，还可以对指定的一行代码进行评论（图 1.4）。通过这一功能，开发者们可以针对具体的代码进行讨论，使代码审查的工作变得前所未有地惬意

![Alt text](./1583072700872.png)

### 3.1 Social Coding

随着 GitHub 的出现，软件开发者们才真正意义上拥有了源代码。世界上任何人都可以比从前更加容易地获得源代码，将其自由更改并加以公开。如今，世界众多程序员都在通过 GitHub 公开源代码，同时利用 GitHub 支持着自己日常的软件开发。

在 GitHub 出现之前，软件开发中只有一小部分人拥有更改源代码的权利，**这个特权阶级掌握着开发的主导权**。开发者在改写、发布源代码之外，往往需要花更多时间和精力去说服这个特权阶级。这导致了许多起初效率很高的流行软件越发保守化，最终被时代所抛弃。

但是，GitHub 的出现为软件开发者的世界带来了真正意义上的“民主”，让所有人都平等地拥有了更改源代码的权利。这在软件开发领域是一场巨大的革命。而革命领导者 GitHub 的口号便是“社会化编程”。

### 3.2 GitHub 最大的特征是“面向人”

GitHub 与以往的仓库托管服务最大的不同点，就在于它以人为中心。

以往的仓库托管服务都是以项目为中心，每个项目就是一个信息封闭的世界。虽然能够知道一个仓库的管理者是谁，但这个管理者还在做哪些事，我们就不得而知了。

GitHub 除项目之外，还可以把注意力集中到人身上。我们不但**能阅览一个人公开的所有源代码**，只要查看其控制面板中的 **News Feed**，还能知道他**对哪些仓库感兴趣**，什么时候做过提交等。一个人在 GitHub 进行的开发是一目了然的 。

您可以将注意力聚焦到感兴趣的人身上。他既可以是您崇拜已久的超级黑客，也可以是同校同学或公司的同事。

能同时关注人与代码，是 GitHub 为我们带来的一个新的世界。

## 4. 全局初始配置

### 4.1 Git 安装

#### 4.1.1  Mac

Mac 中都预装了 Git。而各版本的 Linux 中也都以软件包（Package）的形式提供给用户了，所以各位可以直接使用。

#### 4.1.2 Windows

下载[Git for Windows](https://gitforwindows.org/)
> 原地址： http://msysgit.github.io/

- 选择 Use Git Bash only 
- **换行符的转换**: 选择 **Checkout Windows-style, commit Unix-style line endings**
> GitHub 中公开的代码大部分都是以 Mac 或 Linux 中的 **`LF`**（`Line Feed`）换行。然而，由于 Windows 中是以 **`CRLF`**（`Carriage Return ＋ Line Feed`）换行的，所以在非对应的编辑器中将不能正常显示。
> 
>  Git 可以通过设置自动转换这些换行符。使用 Windows 环境的各位，请选择推荐的“Checkout Windows-style, commit Unix-style line endings”选项。换行符在签出时会自动转换为 CRLF，在提交时则会自动转换为 LF。
>   
>  (摘自《Github入门与实践 -2.3 安装》)

### 4.2 设置姓名和邮箱地址

```vim
$ git config --global user.name "Firstname Lastname"
$ git coffig --global user.email "your_emal@example.com"
```

这个命令，会在“`~/.gitconfig`”中以如下形式输出设置文件。

```vim
[core]
	editor = \"D:\\program files\\Microsoft VS Code\\Code.exe\" --wait
[user]
	name = VarianWrynn
	emal = yuna1111@163.com
```

备注：
“`~/.gitconfig`”这个文件是存在`C:\Users\UserName`目录下

![@||480x0](./1583288741208.png)

### 4.3 提高命令输出的可读性

顺便一提，将 color.ui 设置为 auto 可以让命令的输出拥有更高的可读性。	

```vim
$ git config --global color.ui auto
```

“~/.gitconfig”中会增加下面一行:

![@||480x0](./1583290261651.png)


### 4.4 通过命令行查看config全局配置

```g
git config --global --list
```


## 5. 设置 SSH Key
> 参考 [Generating a new SSH key and adding it to the ssh-agent](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

GitHub 上连接已有仓库时的认证，是通过使用了 SSH 的公开密钥认证方式进行的。现在让我们来创建公开密钥认证所需的 SSH Key，并将其添加至 GitHub。已经创建过的读者，请用现有的密钥进行设置。

运行下面的命令创建 SSH Key。

```vim
$ ssh-keygen -t rsa -C "your_email@example.com"
Generating public/private rsa key pair.
Enter file in which to save the key
(/Users/your_user_directory/.ssh/id_rsa): 按回车键
Enter passphrase (empty for no passphrase): 输入密码
Enter same passphrase again: 再次输入密码
```

输入密码后会出现以下结果。

![@||500x0](./1583316191873.png)

**`id_rsa`** 文件是私有密钥，**`id_rsa.pub`** 是公开密钥。


### 5.1 添加公开密钥

**在 GitHub 中添加公开密钥，今后就可以用私有密钥进行认证了**。首先需要查找到Github你账号下面设置的公钥，这个公钥存储在`id_rsa.pub`中。

**id_rsa.pub 的内容可以用如下方法查看**。

```vim
$ cat ~/.ssh/id_rsa.pub
```

![Alt text](./1583316788980.png)






点击右上角的账户设定按钮（[Settings](https://github.com/settings/keys)），选择 SSH Keys 菜单之后，就会出现如图3.2的界面。

![@||800x0](./1583317314968.png)










点击Add SSH Key，会出现Title和Key两个输入框。在 Title 中输入适当的密钥名称。Key 部分请粘贴 id_rsa.pub 文件里的内容。

添加完出现如下的报错，原因是因为**没有**把开头的`ssh-rsa`一起复制上。
![@||400x0](./1583318525517.png)



一起复制上之后添加就通过了：
![Alt text](./1583319015453.png)










### 5.2 SSH通讯验证
添加成功之后，创建账户时所用的邮箱会接到一封提示“公共密钥添加完成”的邮件。

![@||300x0](./1583319428139.png)









完成以上设置后，就可以用手中的私人密钥与 GitHub 进行认证和通信了。让我们来实际试一试。

```vim
$ ssh -T git@github.com
The authenticity of host 'github.com (207.97.227.239)' can't be established.
RSA key fingerprint is fingerprint值 .
Are you sure you want to continue connecting (yes/no)? 输入yes
```

出现如下结果即为成功。

```vim
Hi VarianWryy! You've successfully authenticated, but GitHub does not provide shell access.
```
![@第一次为密码输错||](./1583319635240.png)

> 这里出现 **Enter passphrase for key '/c/Users/lee.wang/.ssh/id_rsa':** 需要注意输入密码。
> 2020-12-14

### 5.3 SSH可能并不校验邮箱

这个小结是我在操作完 `6-牛刀小试`之后观察到的。在执行 `git push`命令之后，我调用`git log`查看，发现Author这个栏位是这样的：
![@||550x0](./1583994118097.png)

但是这个邮箱是不存在的，或者即便存在，也不可能是我的。应该是当初配置的时候不小心写错了。

我一开始刚到很奇怪，为什么写错的邮箱也能校验通过，我特意到存储公钥的文件里面查询（`$ cat ~/.ssh/id_rsa.pub`）：

![@||600x0](./1583994258246.png)

这个邮箱是公司的邮箱，我用的也是公司的电脑。但是我用这个 `ssh-rsa` 公钥到github上注册添加了。

由此可见，**Github校验只校验你的SSH是否注册了，并不会校验邮箱等信息，也不在乎这个邮箱是否曾经在Github上注册过**。

那么最后一个问题，如果用一个不存在的邮箱`push`了代码，github上会怎么显示呢？

![@||400x0](./1583994432017.png)

可以看到，就是一个default的头像和提交的时候的名字，这个头像无法点击查看。


最后，我在git的配置文件中找到了那个不存在的邮箱：
![@||600x0](./1583995554711.png)


该文件夹默认是在 `C:\Users\{你的电脑名称}`目录下：
![@||360x0](./1583995607772.png)


## 6. 牛刀小试

### 6.1 Clone

![Alt text](./1616391914883.png)


clone 已有仓库。  

**S1： 打开目标仓库，然后点击【Clone or download】按钮，复制如下的地址。**

![@||400x0](./1583989312887.png)


**S2： 打开本地git客户端，执行`git clone`命令：**

```
$ git clone git@github.com:VarianWrynn/Tutorial.git
```

执行结果：成功讲项目从github上克隆到本地：
![@||600x0](./1583989361709.png)

**S3： 切换到该项目**

看到该项目已经成功clone到了本地:

......................
```
$ cd Tutorial/
```

![@||460x0](./1583989493131.png)

![@||300x0](./1583991478930.png)


**S4： 在该项下面手工新增一个text文本，然后使用 `git status`命令查看**

![@||500x0](./1583991113373.png)

由于 **Lee2020-3-12.txt** 还没有添加至 Git 仓库，所以显示为 **Untracked files**。


### 6.2 Submit

将  **Lee2020-3-12.txt**  提交至仓库。这样一来，这个文件就进入了版本管理系统的管理之下。今后的更改管理都交由 Git 进行。

**S1：通过 git add命令将文件加入暂存区** 

在 **Index 数据结构**中记录文件提交之前的状态。

**S2: 再通过 git commit命令提交。**

![@||600x0](./1583991921387.png)

 **S3: git log命令查看提交日志。**

![@||600x0](./1583992001109.png)

### 6.3 push
完成`git add`、`git commit`之后，打开github页面依然看不到新增的文件。

![@||600x0](./1583992281893.png)

这时候需要执行 `push` 命令，GitHub 上的仓库就会被更新。

```
Lenovo@DESKTOP-PBJEFFJ MINGW64 ~/Tutorial (Tutorial_Branch)
$ git push
Warning: Permanently added the RSA host key for IP address '140.82.113.4' to the list of known hosts.
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 335 bytes | 335.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:VarianWrynn/Tutorial.git
   74e5020..82d5113  Tutorial_Branch -> Tutorial_Branch
```

这时候再刷新github就出现了：
![@||600x0](./1583992503696.png)









这样一来代码就在 GitHub 上公开了。



## 7. 推送至远程仓库

在 GitHub 上新建一个仓库。为防止与其他仓库混淆，仓库名请与本地仓库保持一致。

创建时请不要勾选 **`Initialize this repository with a README`** 选项。因为一旦勾选该选项，GitHub 一侧的仓库就会自动生成 README 文件，从创建之初便与本地仓库失去了整合性。


![@||400x0](./1616310477372.png)





虽然到时也可以强制覆盖，但为防止这一情况发生还是建议不要勾选该选项，直接点击 Create repository 创建仓库。

### 7.1 git remote add——添加远程仓库

在 GitHub 上创建的仓库路径为“**git@github.com:用户名/DesignPatternPractise.git**”。现在我们用 **`git remote add`**命令将它设置成本地仓库的远程仓库 

![Alt text](./1616310499407.png)


```
$ git remote add origin git@github.com:VarianWrynn/DesignPatternPractise.git
```

按照上述格式执行 `git remote add` 命令之后，Git 会自动将 `git@github.com:VarianWrynn/DesignPatternPractise.git`远程仓库的名称设置为 origin（标识符）。


![Alt text](./1616310547817.png)


> [参考：git remote 使用总结（简书）](https://www.jianshu.com/p/83c7ffc9b259)

### 7.2 git push——推送至远程仓库

如果想将当前分支下本地仓库中的内容推送给远程仓库，需要用到 git push命令。现在假定我们在 master 分支下进行操作。

```
$ git push -u origin master

Enter passphrase for key '/c/Users/leewo/.ssh/id_rsa':
Enumerating objects: 41, done.
Counting objects: 100% (41/41), done.
Delta compression using up to 8 threads
Compressing objects: 100% (33/33), done.
Writing objects: 100% (41/41), 248.15 KiB | 1.18 MiB/s, done.
Total 41 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), done.
To github.com:VarianWrynn/DesignPatternPractise.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.

```
像这样执行 `git push`命令，当前分支的内容就会被推送给远程仓库 `origin` 的 `master` 分支。

**`-u`** 参数可以在推送的同时，将 origin 仓库的 master 分支设置为本地仓库当前分支的 **upstream（上游）**。

添加了这个参数，将来运行 `git pull`命令从远程仓库获取内容时，本地仓库的这个分支就可以直接从 origin 的 master 分支获取内容，省去了另外添加参数的麻烦。

执行该操作后，当前本地仓库 master 分支的内容将会被推送到 GitHub 的远程仓库中。在 GitHub 上也可以确认远程 master 分支的内容和本地 master 分支相同。

现在就可以在**https://github.com/VarianWrynn/DesignPatternPractise**上看到被推送上来的项目了。


### 7.3 推送至 master 以外的分支
除了 **master** 分支之外，远程仓库也可以创建其他分支。举个例子，我们在本地仓库中创建 **feature-D** 分支，并将它以同名形式 push 至远程仓库。

```
$ git checkout -b feature-D
Switched to a new branch 'feature-D'
```

我们在本地仓库中创建了 feature-D 分支，现在将它 push 给远程仓库并保持分支名称不变。

```
$ git push -u origin feature-D

Total 0 (delta 0), reused 0 (delta 0)
To git@github.com:github-book/git-tutorial.git
 * [new branch]      feature-D -> feature-D
Branch feature-D set up to track remote branch feature-D from origin.
```

现在，在远程仓库的 GitHub 页面就可以查看到 feature-D 分支了。