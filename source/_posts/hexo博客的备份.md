---
title: hexo博客的备份
tags:
  - Hexo
  - 命令
categories: Hexo
abbrlink: 46eab5cb
date: 2020-07-11 15:13:54
---

相关的hexo仓库备份策略，用于多地同时编辑及备份

<!-- more -->

新建博文

```shell
Hexo n "name_of_file"
```

清空数据库旧记录
```shell
Hexo clean
```
生成新记录
```shell
Hexo g
```
把生成的页面推送上去GitHub
```shell
Hexo d
```
---

把源文件也推送上去GitHub：

在根目录下进行Git初始化
```shell
git init
```
**创建源文件分支，命名为blog，用来存放源码【重点】**

```shell
git checkout -b blog
```
文件添加 并 提交
```shell
git add.
git commit -m 'backup'
```
添加远程仓库
```shell
git remote add origin git@github.com:UserName/UserName.github.io.git
```
push到blog分支
```shell
git push origin blog
```






相关连接：

- [参考链接](https://www.yansheng.xyz/article/b4e9a9a2.html)1
- [参考链接](https://blog.csdn.net/zk673820543/article/details/52698760)2

