---
title: "Use hugo-PaperMod to build a blog"
date: 2024-11-10
draft: false
author: "Chen Xi"
tags: ["blog", "tutorial"]
categories: ["tech note"]
---
# 1. 安装hugo

https://gohugo.io/installation/windows/

`winget install Hugo.Hugo.Extended`

# 2. 创建hugo站点

`hugo new site MyFreshWebsite --format yaml`

# 3. 安装paper-mod主题

进入MyFreshWebsite文件夹之后，`git init`初始化git后使用以下命令安装paper-mod主题。

`git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod`

# 4. 修改config.yaml配置个性化网站

阅读官方文档了解各配置含义

使用exampleSite中的配置文件

# 5. 发布第一条博文
使用hugo new post/my-first-post.md创建博文

使用hugo server -D启动本地服务器查看博文

