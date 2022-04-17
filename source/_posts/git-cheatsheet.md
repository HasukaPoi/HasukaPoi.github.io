---
title: git cheatsheet
date: 2022-4-17 10:49:58
tags:
---

就是说命令行确实很难记，但比起满世界找好用的GUI工具（不如……自己写一个？），还是记吧。

这本自用的cheatsheet，不作罗列，按场景区分。

<!-- more -->

## git reset

～想要撤销commit的时候～

首先有这三个概念。版本库——所有commit过的东西。暂存区——用git add添加了但还没有提交的东西。工作区——在本地修改了的东西。

这三个区是逐级递进的。工作区改东西→添加到暂存区→把暂存区的东西提交。

正好，就对应了`git reset`的三个选项，`--soft` `--mixed` `--hard`。其中mixed是默认选项。

而`git reset`做的最主要的事情是什么呢。是**重设**HEAD指针指向的的位置。就比如说原本是下面这个样子的。

```
commit A --> commit B --> commit C --> commit D
                                        |
                                       HEAD
```

执行了`git reset C`或者`git reset --mixed C`之后呢指针就变成这样了。

```
commit A --> commit B --> commit C --> commit D
                           |
                          HEAD
```

那里面的文件呢？**除了hard以外**，mixed和soft都不会对本地文件做出变更。
soft时，对暂存区、工作区不改动。使用场景：？
mixed时，会把目标版本之后的版本丢到暂存区。使用场景举例：改了一些东西之后觉得这些东西可以和前几个版本合并成一个commit更干净，可以直接 reset 再 commit。
hard时，会清空暂存区和工作区。使用场景举例：彻底回滚，放弃修改。


