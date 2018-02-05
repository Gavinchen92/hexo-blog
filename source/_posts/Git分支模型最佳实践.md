---
title: Git分支模型最佳实践
date: 2018-01-04 00:40:45
tags:
---

今天读了[@nvie](http://twitter.com/nvie)的博文[A successful Git branching model](http://nvie.com/posts/a-successful-git-branching-model/), 是在觉得很棒， 写点笔记吧.

现放张图(其实这张图已经高度概括了文章的重点):

![A successful Git branching model](/images/git-model.png)

### 分散同时是集中的

为什么这么说？git 允许存在多个分支, 甚至每个人都有自己的分支, 但是这些分支的起源都是一样的, 即有一个中心分支

### 主要分支

* master
* develop

这两个分支的生命是无限的, 其他分支都有生命周期

master 分支与生产环境保持一致, develop 的代码一直保持最新

### 辅助分支

辅助分支分三种类型

* Feature 分支
* Release 分支
* Hotfix 分支

#### Feature 分支

该分支作为开发新功能使用, 一般不会推送到 origin

来至于: 大部分是 develop
分支最终将被合并到: develop 分支

#### Release 分支

将会作为一个预发布版本， Release 上面之允许修改 bug， 一般不允许增加新功能

来至于: develop 分支

分支最终将被合并到: develop 分支和 master 分支

#### Hotfix 分支

这是一个零时分支， 主要目的是为了解决生产环境的紧急 bug

来至于: master 分支

分支最终将被合并到: develop 分支和 master 分支

有一个特殊情况当 release 和 hotfix 同时存在时, hotfix 将会合并到 release
