---
title: Pointer in Python
date: 2021-08-24T14:49:09+08:00
lastmod: 2021-08-24T14:49:09+08:00
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

Simulating pointer in python.

<!--more-->

## Mutable and immutable value in memory

For immutable value like integer, consider the code below:

```python
a = 10
b = a
b = 20
```

After that, a will equal to 10 and b will equal to 20. The pictures demonstrate the memory behind the code:

![](/img/202108241508.svg)

We  can find the name of the value is actually a pointer, but we can't use them in immutable value, because we can't change the value pointed.

For mutable value like list, consider the code below:

```python
a = [1,2,3,4]
b = a
b.append(5)
```

After that, both a and b will be [1,2,3,4,5], the memory usage is like:

![](/img/202108241532.svg)

By this property in mutable value, we can simulate pointer like c++.

## Using mutable value simulate pointer

Take linked list by python as an example. This is the second question in LeetCode, Add two numbers.

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
```

```python
class Solution:
    def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
        head = ListNode()
        p1 = head
        p2 = (l1,l2)
        d = 0
        while True:
            if p2[0] and p2[1]:
                value, s = ((p2[0].val + p2[1].val + d)%10),((p2[0].val + p2[1].val + d)//10)
                p1.next = ListNode(value)
                p1 = p1.next
                p2 = (p2[0].next,p2[1].next)
                d = s
            elif p2[0]==None and p2[1]!=None:
                value, s = ((p2[1].val + d)%10,(p2[1].val + d)//10)
                p1.next = ListNode(value)
                p1 = p1.next
                p2 = (p2[0],p2[1].next)
                d = s
            elif p2[0]!=None and p2[1]==None:
                value, s = ((p2[0].val + d)%10,(p2[0].val + d)//10)
                p1.next = ListNode(value)
                p1 = p1.next
                p2 = (p2[0].next,p2[1])
                d = s
            elif p2[0]==None and p2[1]==None and d!=0:
                p1.next = ListNode(d)
                d=0
            elif p2[0]==None and p2[1]==None and d==0:
                break
        return head.next
```

In this example, p1 and p2 are pointers.
