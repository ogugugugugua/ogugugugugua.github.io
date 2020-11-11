---
title: 搭建个人博客Hexo
categories: Hexo
tags:
  - hexo
  - 命令
abbrlink: b085374e
date: 2020-01-01 15:40:15
---

## 如何使用Hexo来搭建个人博客？

本文的操作环境基于Windows10系统，生成文件部署与GitHub上，使用阿里云的个人域名进行重定向。

 <!-- more -->

1. 安装node，npm，cnpm，hexo
```shell
---	#安装Nodejs
node -v	#查看node版本
npm -v	#查看npm版本
npm install -g cnpm --registry=http://registry.npm.taobao.org	#安装淘宝的cnpm 管理器
cnpm -v	#查看cnpm版本
cnpm install -g hexo-cli    #安装hexo框架
hexo -v	#查看hexo版本
```
2. 创建文件夹blog，进入该文件夹，初始化hexo，启动本地博客服务，尝试访问本地地址来查看效果
```shell
# mkdir blog	#创建blog目录
# cd blog	 #进入blog目录
hexo init 	#生成博客 初始化博客
hexo s	#启动本地博客服务
http://localhost:4000/	#本地访问地址
```
3. 新建文章，修改内容。
   清理旧记录，创建新记录。
```shell
hexo n "我的第一篇文章" #创建新的文章 
#返回blog目录
hexo clean #清理
hexo g #生成
```
4. 在GitHub上创建一个新的仓库`YourGithubName.github.io`。【注意】需要保持第一个前缀与用户名完全一致，这是GitHubPages的要求。
   使用cnpm安装git部署插件
```shell
#Github创建一个新的仓库 YourGithubName.github.io
cnpm install --save hexo-deployer-git #在blog目录下安装git部署插件
```
5. 在Hexo的配置文件`_config.yml`中添加GitHub的相关配置
```shell
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
    type: git
    repo: https://github.com/YourGithubName/YourGithubName.github.io.git
    branch: master
```
6. 将本地仓库部署到GitHub上，访问对应的GitHubPages
```shell
hexo d	#部署到Github仓库里
https://YourGithubName.github.io/  #访问这个地址可以查看博客
```
7. 下载合适的Hexo主题，修改Hexo配置文件以调整主题，访问对应的GitHubPages
```shell
 git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia  #下载yilia主题到本地
 
#修改hexo根目录下的 _config.yml 文件 ： theme: yilia
hexo c	#清理一下
hexo g	#生成
hexo d	#部署到远程Github仓库
https://YourGithubName.github.io/  #查看博客
```

8. 个性化域名：

   GitHubPages可以接受www, blog, @这三种域名前缀。
   1. 修改阿里云域名解析设置（推荐使用非顶级域名，即这里的主机记录设置为非@）：

      | 主机记录 | 记录类型 | 解析线路 | 记录值                   |
      | -------- | -------- | -------- | ------------------------ |
      | blog     | CNAME    | 默认     | YourGithubName.github.io |
   2. 在本地目录中的source目录下，新建不带后缀的CNAME文件，在里面添加自己的域名，如[blog.yulin.cool](https://blog.yulin.cool)，即本站。然后hexo c; hexo g; hexo d; 将本地的变化推送到GitHub仓库上。
   3. 在GitHub上进行设置：点击repo中的Settings设置，找到Custom domain，填上自己的域名，比如[blog.yulin.cool](https://blog.yulin.cool)。