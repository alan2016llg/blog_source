---
title: 搭建hexo个人博客
categories:
  - Other
tags:
  - Other
date: 2020-01-11 01:08:23
---

### 目录
* [1.缘由](#1-缘由)
* [2.目的](#2-目的)
* [3.具体实施](#3-具体实施)
    * [3.1 事前准备](#3-1事前准备)
    * [3.2 实施并验证](#3-2实施并验证)
* [4.为什么采用以上方式](#4-为什么采用以上方式)

## 1.缘由

快速搭建个人博客，简单方便易上手

## 2.目的

写写个人博客，记录记录

## 3.具体实施

直接fork代码，修改参数，运行即可


### 3.1事前准备

1.  github账号
2.  本地安装npm
3.  安装hexo
4.  安装git客户端
5.  clone代码
6.  修改相关配置
7.  提交github
8.  finish

### 3.2实施并验证

1.  假设已有github账号，且本地已安装git客户端，且已配置相关ssh-key
2.  选择一个目录，git clone git@github.com:alan2016llg/blog_source.git
3.  cd bolg_source  mkdir themes/3-hexo
4.  git clone git@github.com:alan2016llg/hexo-theme-3-hexo.git themes/3-hexo
5.  下载安装node,并通过npm安装hexo，提交git还需npm install --save hexo-deployer-git
6.  修改blog_source下的_config.yml配置
7.  修改blog_source/themes/3-hexo/_config.yml配置
8.  hexo clean
9.  hexo g   // 构建
10.  hexo s  //本地启动查看
11.  在github上创建一个放置静态的仓库，配置blog_source/themes/3-hexo/_config.yml也要修改
12.  hexo d  //部署到github
13.  在创建的静态仓库中选择Settings,下拉到GitHub Pages选择
14.  访问


## 4.为什么采用以上方式


快速搭建
