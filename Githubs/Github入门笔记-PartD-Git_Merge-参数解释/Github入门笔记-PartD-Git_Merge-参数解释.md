# Github入门笔记-PartD  Git Merge 参数解释
@(读书笔记组)[GitHub, GitHub 101, GitHub 漫游指南, Git工作流程, 阮一峰, Github入门笔记]

[toc]



* [Github入门笔记\-PartD  Git Merge 参数解释](#github入门笔记-partd--git-merge-参数解释)
  * [1\. 基本操作](#1-基本操作)
  * [2\.  Git 合并时 \-\-no\-ff 的作用](#2--git-合并时---no-ff-的作用)
  * [3\. 小结](#3-小结)
  * [4\. 相关问题](#4-相关问题)
    * [Pulling without specifying how to reconcile divergent branches is discouraged](#pulling-without-specifying-how-to-reconcile-divergent-branches-is-discouraged)
  * [5\. References &amp; Connection](#5-references--connection)
  * [6\. 文档修订记录](#6-文档修订记录)





##  1. 基本操作

> 摘录：《Gihub入门与实践》 4.2章节。

分支 feature-A 已经实现完毕，想要将它合并到主干分支 master 中。首先切换到 master 分支。

```
$ git checkout master
Switched to branch 'master'
```

然后合并 feature-A 分支。为了在历史记录中明确记录下本次分支合并，我们需要创建合并提交。因此，在合并时加上 --no-ff参数。

```
$ git merge --no-ff feature-A
```

随后编辑器会启动，用于录入合并提交的信息。

```
Merge branch 'feature-A'
    　
# Please enter a commit message to explain why this merge is necessary,
# especially if it merges an updated upstream into a topic branch.
#
# Lines starting with '#' will be ignored, and an empty message aborts
# the commit.
```

默认信息中（Merge branch 'feature-A'）已经包含了是从 feature-A 分支合并过来的相关内容，所以可不必做任何更改。将编辑器中显示的内容保存，关闭编辑器，然后

就会看到下面的结果。

```
Merge made by the 'recursive' strategy.
 README.md | 2 ++
 1 file changed, 2 insertions(+)
```

这样一来，feature-A 分支的内容就合并到 master 分支中了。


## 2.  Git 合并时 --no-ff 的作用

在许多介绍 Git 工作流的文章里，都会推荐在合并分支时，加上 `--no-ff` 参数：

```
$ git checkout develop
$ git merge --no-ff feature
```

`--no-ff` 在这的作用是禁止快进式合并。

Git 合并两个分支时，如果顺着一个分支走下去可以到达另一个分支的话，那么 Git 在合并两者时，只会简单地把指针右移，叫做“快进”（fast-forward），比如下图：

```
          A---B---C feature
         /
D---E---F master
```


要把 feature 合并到 master 中，执行以下命令：

```
$ git checkout master
$ git merge feature
```

结果就会变成：

```
          A---B---C feature
         /         master
D---E---F 
```

![@||700x0](./ff.gif)














因为 feature 就在 master 的下游，所以直接移动了 master 的指针，master 和 feature 都指向了 C。而如果执行了 `git merge --no-ff feature` 的话，是下面的结果：

```
          A---B---C feature
         /         \
D---E---F-----------G master
```


![@||700x0](./noff.gif)












由于 `--no-ff` 禁止了快进，所以会生成一个新的提交，master 指向 G。

## 3. 小结

从合并后的代码来看，结果其实是一样的，区别就在于 --no-ff 会让 Git 生成一个新的提交对象。

为什么要这样？通常我们把 master 作为主分支，上面存放的都是比较稳定的代码，提交频率也很低，而 feature 是用来开发特性的，上面会存在许多零碎的提交，快进式合并会把 feature 的提交历史混入到 master 中，搅乱 master 的提交历史。

所以如果你根本不在意提交历史，也不爱管 master 干不干净，那么 --no-ff 其实没什么用。

不过，如果某一次 master 出现了问题，你需要回退到上个版本的时候，比如上例，**你就会发现退一个版本到了 B，而不是想要的 F，因为 feature 的历史合并进了 master 里**。


## 4. 相关问题

### Pulling without specifying how to reconcile divergent branches is discouraged

![@||600x0](./1615186816972.png)










> In its default mode, `git pull` is shorthand for `git fetch` followed by `git merge` FETCH_HEAD.

When you do a `git pull origin master`

git pull performs a merge, which often creates a merge commit. Therefore, by default, pulling from the remote is NOT a harmless operation: it can create a new commit sha that didn’t exist before. This behavior can confuse a user, because what feels like it should be a harmless download operation actually changes the commit history in unpredictable ways.

To avoid this, you need:

```vim
git pull --ff-only
```

or not? read on to see which one fits your needs)

With `git pull --ff-only`, Git will update your branch only if it can be “fast-forwarded” without creating new commits. If this can’t be done, `git pull --ff-only` simply aborts with an error message.


You can configure your Git client to always use `--ff-only` by default, so you get this behavior even if you forget the command-line flag:

```vim
git config --global pull.ff only
```

Note: The `--global` flag applies the change for all repositories on your machine. If you want this behaviour only for the repository you're in, omit the flag.


Taken from [here](https://blog.sffc.xyz/post/185195398930/why-you-should-use-git-pull-ff-only)

1. [How to deal with this git warning? “Pulling without specifying how to reconcile divergent branches is discouraged”](https://stackoverflow.com/questions/62653114/how-to-deal-with-this-git-warning-pulling-without-specifying-how-to-reconcile)


## 5. References & Connection
1. [工具系列 | Git 合并时 --no-ff 的作用 --开源技术小栈的微信公众号](https://mp.weixin.qq.com/s/zME846v1ZyU3ee476phyIQ)
2. [CS Visualized: Useful Git Commands --Lydia Hallie](https://dev.to/lydiahallie/cs-visualized-useful-git-commands-37p1?signin=true)
3. [10 个迅速提升你 Git 水平的提示【转】](https://www.cnblogs.com/sky-heaven/p/6000494.html)
4. [Git 命令收集](https://www.cnblogs.com/hongdada/p/9549506.html)

## 6. 文档修订记录

| 版本号|     变化状态|   简要说明|  日期	|   变更人/参与者   |
| :-------- | :--------| :------ |:------ |:------ |
| V1.0|   建立| 文档初建 |2021-3-8 | Lee|

*变化状态：建立，修改，增加，删除







