# Github入门笔记-PartH-删除所有commit历史记录
@(读书笔记组)[GitHub, GitHub 101, GitHub 漫游指南, Git工作流程, Github入门笔记]



[toc]

* [Github入门笔记\-删除所有commit历史记录](#github入门笔记-删除所有commit历史记录)
  * [操作](#操作)
  * [6\. References &amp; Connections](#6-references--connections)
  * [7\. 文档修订记录](#7-文档修订记录)



<img src="./1616476281619.png" alt="Alt text" style="zoom: 80%;" />






## 1. 删除所有的commit记录


```shell
$ git checkout --orphan=main
Switched to a new branch 'main'
```

<img src="./1616476879894.png" alt="Alt text" style="zoom:80%;" />

<img src="./1616476887158.png" alt="Alt text" style="zoom:80%;" />


```shell
git add -A
```

```shell
$ git commit -m "to avoid access key leaking"

[main (root-commit) cf13cd3] to avoid access key leaking
 1758 files changed, 352534 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 CMSProjectsV2/NBCMS.BLL/NBCMS.BLL.csproj
 create mode 100644 CMSProjectsV2/NBCMS.BLL/Properties/AssemblyInfo.cs
 ......
```


```shell
$ git branch -D master
Deleted branch master (was d0364b1).
```

```shell
$ git branch -m master
```

<img src="./1616477143402.png" alt="Alt text" style="zoom:80%;" /


```shell
$ git push -f origin master
```



## 2. 查看当前仓库的历史提交记录



```shell
git shortlog -s -n
```

<img src="./image-20210915091318281.png" alt="image-20210915091318281" style="zoom:80%;" />

## 6. References & Connections

1. [how to delete all commit history in github? --StatckOverflow](https://stackoverflow.com/questions/13716658/how-to-delete-all-commit-history-in-github)
2. [What is `git checkout --orphan` used for?--Stackoverflow](https://stackoverflow.com/questions/19980631/what-is-git-checkout-orphan-used-for)


## 7. 文档修订记录
| 版本号|     变化状态|   简要说明|  日期	|   参与者   |
| :-------- | :--------| :------ |:------ |:------ |
| V1.0|   建立| 文档初建|2021-3-21| Lee|

*变化状态：建立，修改，增加，删除



