---
title: Python mutable and immutable objects
date: 2021-08-20T16:25:34+08:00
lastmod: 2021-08-20T16:25:34+08:00
author: Erwin
# avatar: /img/author.jpg
# authorlink: https://author.site
# cover: /img/cover.jpg
# images:
#   - /img/cover.jpg
categories:
  - python
tags:
  - python
# nolastmod: true
draft: false
---

Illuminating the difference between mutable and immutable objects in python

<!--more-->

## Mutable objects

The location of mutable objects will be changed when reassign value to it, it will not change when change the value.

Mutable objects contain list, dictionary, set and custom classes.

```python
class person:
    def __init__(self,name):
        self.name = name

a = person("Li")
b = a
a.name, b.name
```

    ('Li', 'Li')

```python
id(a), id(b)
```

    (140342160258672, 140342160258672)

```python
a.name = "Wang"
```

```python
a.name, b.name
```

    ('Wang', 'Wang')

```python
id(a), id(b)
```

    (140342160258672, 140342160258672)

```python
l1 = [1,2,3]
l2 = l1
l1, l2
```

    ([1, 2, 3], [1, 2, 3])

```python
id(l1), id(l2)
```

    (140342160434432, 140342160434432)

```python
l2.append(2)
l1, l2
```

    ([1, 2, 3, 2], [1, 2, 3, 2])

```python
id(l1), id(l2)
```

    (140342160434432, 140342160434432)

## immutable objects

The location of immutable objects will be changed when the value be changed, if location don't be changed, the value can't be changed too.

Immutable objects contain float, integer, tuple, string and frozenset.