---
title: Git basic operation
date: 2021-08-24T16:34:38+08:00
lastmod: 2021-08-24T16:34:38+08:00
author: Erwin
# avatar: /img/author.jpg
# authorlink: https://author.site
# cover: /img/cover.jpg
# images:
#   - /img/cover.jpg
categories:
  - git
tags:
  - instruction
# nolastmod: true
draft: false
---

Basic usage of git and github.

<!--more-->

Global configuration:

```bash
git config --global user.name "your name"
git config --global user.email "you email"
```

Basic Usage:

```bash
git init                              # 在当前目录初始化git repository
                                      # initiate a git repository in current directory
git add --all                         # 追踪当前目录下所有文件
                                      # track all file in repository
git commit -m "xx"                    # 提交变化
                                      # commit change
git remote add origin "remote repo"   # 添加远程仓库
                                      # add remote repository
git branch -M master main             # 分支master改名为main(github默认分支)
                                      # rename this branch from master to main
git push -u origin master/main        # 推送到远程仓库
                                      # push data to remote repository
git log --pretty=format:"%s"          # 查看commit记录
                                      # check commit record
```