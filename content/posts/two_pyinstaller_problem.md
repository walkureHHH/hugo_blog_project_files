---
title: Two pyinstaller problems
date: 2021-08-24T16:34:01+08:00
lastmod: 2021-08-24T16:34:01+08:00
author: Erwin
# avatar: /img/author.jpg
# authorlink: https://author.site
# cover: /img/cover.jpg
# images:
#   - /img/cover.jpg
categories:
  - python
tags:
  - pyinstaller
# nolastmod: true
draft: false
---

Two pyinstaller problems recorded when I first use it.

<!--more-->

## First problem: DistributionNotFound

Wrap python successfully, but raise pkg_resources.DistributionNotFound error when we run the executable file.

![](/img/pyinstaller_1.png)

reference https://github.com/pyinstaller/pyinstaller/issues/1713
and https://stackoverflow.com/questions/34775667/pyinstaller-django-pkg-resources-distributionnotfound-the-django-omnibus

Solution:

Create a python file with content like this in the current directory.

```python
from PyInstaller.utils.hooks import copy_metadata
datas = copy_metadata('prettytable')
```

Than:

```bash
pyinstaller xxx.py --additional-hooks-dir=.
```

## Second problem: Ctrl-C

In my code, Ctrl-C used to break the loop

![](/img/interupt.png)

But after I make executable file by pyinstaller, it performance incorrectly:

![](/img/keyboardinterupt.png)

Method:

```bash
pyinstaller xxx.py --bootloader-ignore-signals
```

