---
title: Boolean series bug
date: 2021-08-24T16:18:36+08:00
lastmod: 2021-08-24T16:18:36+08:00
author: Erwin
# avatar: /img/author.jpg
# authorlink: https://author.site
# cover: /img/cover.jpg
# images:
#   - /img/cover.jpg
categories:
  - python
tags:
  - pandas
# nolastmod: true
draft: false
---

We can't use "in" operator to check if False or True in a boolean series.

<!--more-->

## Problem

Current version: pandas 1.3.2 with python 3.8.5

Example:

```python
a = [False, True, True, True]
b = [True, True]
c = [False, False]

s_a = pd.Series(a)
s_b = pd.Series(b)
s_c = pd.Series(c)
```

Test if "in" can work in list:

```python
True in a, True in b, True in c
```

```python
(True, True, False)
```

```python
False in a, False in b, False in c
```

```python
(True, False, True)
```

Test if "in" can work in Series:

```python
True in s_a, True in s_b, True in s_c
```

```python
(True, True, True)
```

```python
False in s_a, False in s_b, False in s_c
```

```python
(True, True, True)
```

We can find when we use "in" to judge whether True of False in a boolean Series, it must return True.

Test whether "in" is normal for other Series:

```python
1 in pd.Series([1,2,3]), 4 in pd.Series([1,2,3]), 
```

```python
(True, False)
```

So the "in" is normal in integer Series.

## How

We can use all() and any function to check boolean value in Series.

```python
s_a.all(), s_a.any()
```

```python
(False, True)
```

## Summary

We can't use "in" to check whether a boolean value in a Series, we can use all() and any() function replace it.
