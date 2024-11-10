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

# 6. 部署Hugo网站到Github Pages
创建目录
`mkdir -p .github/workflows`

创建工作流文件
`touch .github/workflows/hugo.yaml`

添加以下内容到 hugo.yaml
```name: Deploy Hugo site to Pages

on:
  push:
    branches:
      - main  # 设置要触发部署的分支
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
        with:
          submodules: recursive

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: 'latest'
          extended: true

      - name: Build
        run: hugo --minify

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v2
        with:
          path: ./public

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v2```



