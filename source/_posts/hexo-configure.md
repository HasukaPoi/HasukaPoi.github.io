---
title: 基于 Hexo 和 GitHub Pages 的静态博客的搭建
date: 2019-01-18 15:01:22
tags: 
- 技术
- GitHub
---
## 前情提要

大概半年前？重装系统的时候忘记备份 Hexo 的源文件，然后就。
就没了呗。只剩下之前 deploy 在 GitHub Pages 上的静态 HTML。
然后就一直怠惰直到昨天（2019-01-17）终于开始重建。

## Hexo 是什么

> 快速、简洁且高效的博客框架。

自己去看→ [Hexo 官网](https://hexo.io/)

<!-- more -->

## 在本地创建 Hexo 站点

### 准备工作

> 先安装一些基础的环境。

基本上按照 [Hexo 官方文档：开始使用-概述](https://hexo.io/zh-cn/docs/) 里所说的，首先需要安装 **Git** 和 **Node.js**。这些基础操作不必赘述。Windows 下主要使用 GUI 安装，Mac/Linux 主要使用包管理工具。

### 安装 Hexo

> 安装一个叫做「Hexo」的程序，以便建立「Hexo 站点」。

打开 Git Bash，执行 `npm install -g hexo-cli`。

安装完毕后，`cd` 到站点源代码放置的位置，执行`hexo init`。

> 官网文档里要求再执行一句 `npm install` 来根据目录下的 package.json 来安装默认的一些插件，然而执行完 `hexo init` 之后该装的已经装了。

安装完毕后会生成一些默认的目录结构，先参考 [配置](https://hexo.io/zh-cn/docs/configuration) 来配置 `_config.yml` 中一些基本的网站信息。除此之外我主要关注的文件夹是：
- `/source/`：资源文件夹。其中`/source/_posts`下是日志，其余以下划线开头的文件将被忽略。`.md`和`.html`会被自动解析。
- `/scaffolds/`：模板文件夹。懒得动。
- `/themes/`：主题文件夹。

## 发篇文章看看

执行`hexo new <文件名>`，即可在`source`下生成空白文档。其实跟手动创建区别不大，只是自带了默认的 [Front-matter](https://hexo.io/zh-cn/docs/front-matter)。

语法是 Markdown。目测是 GitHub flavored Markdown。

编辑文档并保存后，即可使用`hexo g`来生成静态网页。生成的页面会放在`/public`下。

使用`hexo s`来启动本地服务器（会自动生成静态网页），然后就可以在 localhost 下使用浏览器预览。

## 部署到 Git
参考 [部署](https://hexo.io/zh-cn/docs/deployment)。本节简述部署到 Git 的操作。
首先安装 [hexo-deployer-git](https://github.com/hexojs/hexo-deployer-git)。
```bash
npm install hexo-deployer-git --save
```

然后在`_config.yml`中找到并修改以下参数：
```yaml
deploy:
- type: git
  repo: <repo url> # https://...
  message: #自定义提交信息，没啥好改的（。
```

配置完毕之后，建议先使用`hexo clean`来清理本地文件，再使用`hexo deploy`来部署。

### 关于 GitHub Pages

1. Repo名务必为：`<用户名>.github.io`
1. 别忘了`CNAME`，如果用自定义域名的话。

## 备份 Hexo 站点本身

在`hexo init`的时候已经自动生成了`.gitignore`文件。
创建一个`README.md`，再：
```bash
git init
git add remote <空repo地址>
git add .
git commit -m "comment"
git push origin master
```
就好了呗……。

## 美化

本博目前使用了 [NexT](https://theme-next.org/) 主题。因为本身已经很好看了所以简单设置之后没有做更多自定义。后略。

## 后记

不知为何觉得有点虎头蛇尾的，不过最核心的部分（建站、部署和备份）已经基本清楚了，剩下的慢慢研究也罢。
毕竟最重要的是内容嘛内容。
感谢您的阅读。
