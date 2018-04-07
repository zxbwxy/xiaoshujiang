---
title: git学习
tags: 新建,模板,小书匠
grammar_cjkRuby: true
---

## git-基本概念

## git-环境设置
1.安装Git
2.自定义Git环境
设置用户名
>$ git config --global user.name "yourname"

设置电子邮箱
>$ git config --global user.email "yourname@email.com"

颜色突出显示
>$ git config --global color.ui true
$ git config --global color.status auto
$ git config --global color.branch auto

设置默认编辑器
>$ git config --global merge.tool vimdiff

列出Git设置
>$ git config --list

## git-生命周期

 - 您将Git存储库作为工作副本进行克隆。
 - 您可以通过添加/编辑文件来修改工作副本。
 - 如有必要，您还可以通过采取其他开发人员的更改来更新工作副本。
 - 您在提交之前查看更改。
 - 您提交更改。如果一切正常，则将更改推送到存储库。
 - 提交之后，如果您意识到有问题，则更正上次提交并将更改推送到存储库。
![工作流程][1]
## git-创建操作
1.创建本地git服务器

2.创建一个裸仓库
## git-克隆操作
我们在Git服务器上有一个裸仓库，汤姆也推出了他的第一个版本。现在，杰瑞可以查看他的变化。克隆操作创建远程存储库的一个实例。
Jerry在他的主目录中创建一个新目录并执行克隆操作。
$ mkdir jerry_repo
$ cd jerry_repo
$ git clone gituser@git.server.com:project.git

## git-基本概念
## git-基本概念
## git-基本概念
## git-基本概念
## git-基本概念
## git-基本概念
## git-基本概念



[Linux基础知识之用户和用户组以及 Linux 权限管理](https://www.linuxidc.com/Linux/2016-10/136251.htm)
[在Windows上搭建Git Server](https://www.cnblogs.com/sumuncle/p/6362697.html)
[GIT 远程仓库：添加远程库、从远程库克隆](https://www.cnblogs.com/wangmingshun/p/5424767.html)
https://blog.csdn.net/txl199106/article/details/40266345


  [1]: http://owx51rlyb.bkt.clouddn.com/%E5%B0%8F%E4%B9%A6%E5%8C%A0/1522377453975.jpg