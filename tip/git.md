---
html:
    embed_local_images: true
    embed_svg: true
    offline: true
    toc: true

export_on_save:
    html: true
---


[TOC]

# git的使用方法

## git的常用操作
- git init	初始化库
- git status  查看当前状态
- git add		将文件加入暂存、加入跟踪
- git branch	查看分支

    +分支名		新建分支

- git checkout	切换分支

    -b	不存在就创建分支

- git commit	提交

    -m+ "提交信息"

- git rm		删除文件并移出版本控制，也就是删除文件并且加入暂存说明文件已经被删除

    **--cached	从暂存区移除但不删除文件，以便在ignore文件中加入该文件**

- git remote	显示远程仓库

    -v		显示网址

- git remote add [shortname] [url]	添加远程仓库
- git remote show [remote-name]		给出远程仓库的详细信息

- git remote rename [oldname] [newname]	重命名远程分支

- git remote rm				移除远程仓库

- git fetch [remote-name]			从远程仓库拉取数据到本地，但并不合并

- git pull				从远程仓库拉取数据并合并到本地当前分支

- **git push [remote-name] [local-branch]:[branch-name]	将本地的库推送到远程库**

| 命令         | 简化  |
|--------------|-------|
| git status   | gits  |
| git add      | gita  |
| git branch   | gitb  |
| git push     | gitp  |
| git remote   | gitr  |
| git commit   | gitc  |
| git checkout | gitch |

## .gitignore的一些使用方法

创建一个名为.gitignore文件

    #	注释

    []	匹配方括号里的任意一个字符

    /	说明要忽略的是目录

    !	保留这个文件

    *	匹配0个或多个字符串

    ?	匹配1个字符串

    -	在两个数字范围之间


## 怎么用ｇit创建一个远程的仓库

**注意两个方法的push之前都要有commit**

### 方法一

1. 先在远程仓库创建仓库
2. 在本地克隆一个仓库
3. 在本地修改文件
4. git push 推送到远程仓库

### 方法二

1. 在本地仓库做好更改和提交
2. 在远程仓库建仓库
3. git push -u origin master将本地的内容提交

## git命令的更多参数

- git branch	查看分支

    +分支名		新建分支

    -v		查看所有分支的最后一次提交

    -d		删除分支,一般用于已经合并的分支

    -D		删除未合并的分支

- git checkout	切换分支

    -b	不存在就创建分支

    --文件名	撤销对文件的修改

- git commit	提交

    -m+ "提交信息"

    -a		跳过暂存，将跟踪过的文件直接提交

    --amend		用暂存区覆盖最后一次提交

- git rm		删除文件并移出版本控制，也就是删除文件并且加入暂存说明文件已经被删除

    -f		如果文件已经被修改或已经加入暂存

    --cached	从暂存区移除但不删除文件，以便在ignore文件中加入该文件

- git remote	显示远程仓库

    -v		显示网址

## git的一些不常用操作

- git mv		重命名文件并加入到缓存

- git config --global core.editor		设定默认启动的文本编辑器

- gitk		可视化工具

- git diff

    缺省值		为工作区与暂存的区别

    --cached或--staged查看暂存与已经提交的区别

- git rebase		衍合，简化提交历史

- git mergetool		合并分支可视化工具

- git show		展示标签

- git tag			打标签（是最近一次提交还是当前状态）

    -a			有附注的标签，加-m加附注

    -s			带签署的标签

    -v			验证标签

    -a+标签+哈希值 为某次提交添加标签

- git log		查看提交

    -数字		最近的几次

    -p		显示每次提交的内容差异

    --stat		只简要显示增减的行数

    --pretty	指定要展示的格式，如short full fuller format:"格式说明"

    %H 提交对象(commit)的完整哈希字串

    %h 提交对象的简短哈希字串

    %T 树对象(tree)的完整哈希字串

    %t 树对象的简短哈希字串

    %P 父对象(parent)的完整哈希字串

    %p 父对象的简短哈希字串

    %an 作者(author)的名字

    %ae 作者的电子邮件地址

    %ad 作者修订日期(可以用 -date= 选项定制格式)

    %ar 作者修订日期,按多久以前的方式显示

    %cn 提交者(committer)的名字

    %ce 提交者的电子邮件地址

    %cd 提交日期

    %cr 提交日期,按多久以前的方式显示

    %s 提交说明

    选项 说明

    -p 按补丁格式显示每个更新之间的差异。

    --stat 显示每次更新的文件修改统计信息。

    --shortstat 只显示 --stat 中最后的行数修改添加移除统计。

    --name-only 仅在提交信息后显示已修改的文件清单。

    --name-status 显示新增、修改、删除的文件清单。

    --abbrev-commit 仅显示 SHA-1 的前几个字符,而非所有的 40 个字符。

    --relative-date 使用较短的相对时间显示(比如,“2 weeks ago”)。

    --graph 显示 ASCII 图形表示的分支合并历史。

    --pretty 使用其他格式显示历史提交信息。可用的选项包括 oneline,short,full,fuller 和 format(后跟指定格式)。

- git push [origin] [tag]	将标签同步到远程库

    --tags			同步所有标签


## 使用时的一些补充

- 推送本地的新分支到远程仓库并同步
- 删除远程分支 git push origin :branch-name


[TOC]