---
title: Hugo instruction
date: 2021-08-19T15:58:43+08:00
lastmod: 2021-08-20T15:58:43+08:00
author: Erwin
# cover: /img/cover.jpg
categories:
  - hugo
tags:
  - hugo
  - blog
  - instruction
draft: False
---

Elementary usage of hugo, recorded when I build this blog.

<!--more-->

## install hugo

```shell
sudo apt install hugo
```

## basic usage

Creat new site

```shell
hugo new site xxxx
# hugo new site yoursite
```

Creat new passage

```shell
hugo new type/name
# hugo new posts/name.md
```

Test

```shell
hugo server -D
# -D means display draft
```

Generate website

```shell
hugo -d path
# path can be defined in config.toml
```

My config.toml

```toml
baseURL = "http://walkurehhh.github.io"
languageCode = "zh-Hans"
enableRobotsTXT = true
title = "LYH's Blog"
theme = "dream"
hasCJKLanguage = true
publishdir = "../publish"

#LavenderBlush
[params]
  background = "#FFF0F5"
  backgroundImage = "/img/1.jpg"
  linkColor = "seagreen"

  # dark mode c48fa4
  defaultDark = true
  backgroundDark = "#c28795"
  backgroundImageDark = "/img/1.jpg"
  darkLinkColor = "darkseagreen"
  # darkNav = true
  # dark404 = true

  images = [""]

  author = "Erwin"
  description = "Li Yuanhao's Blog"
  avatar = "/img/ichigo_square.jpg"
  headerTitle = "Li Yuanhao's Blog"
  motto = "python yyds"
  # maxTags = 5
  # categoriesLimitInHeader = 6 # deprecated
  # headerBottomText = "" # deprecated

  # footerBottomText = ""

  #rss = true

  utterancesRepo = "walkureHHH/utterances_repo"

  # valine = true
  # LEANCLOUD_APP_ID = ""
  # LEANCLOUD_APP_KEY = ""
  # VALINE_LANGUAGE = ""

  email = "erwinli@qq.com"
  #twitter = ""
  #facebook = ""
  #instagram = ""
  # mastodon = ""
  #linkedin = ""
  github = "walkureHHH"
  #stackoverflow = ""
  #codepen = ""

  siteStartYear = 2020

  favicon = "/favicon.ico"

  highlightjs = true
  # highlightjsCDN = "https://cdn.jsdelivr.net/gh/highlightjs/cdn-release/build/highlight.min.js"
  highlightjsExtraLanguages = ["ocaml"]
  highlightjsTheme = "gruvbox-light"
  highlightjsThemeDark = "gruvbox-dark"

  # search
  enableSearch = true

  # options
  showSummaryCoverInPost = true
  # hasTwitterEmbed = true
  # reversePostAndAside = true
  # shareInAside = true
  fixedNav = true
  # collapsibleTags = true
  # collapseBySummary = true

  [params.advanced]
    customCSS = ["css/background.css"]
    # customJSBefore = []
    # customJS = []

  [params.experimental]
    jsDate = true
    jsDateFormat = "yyyy-MM-dd"
```

