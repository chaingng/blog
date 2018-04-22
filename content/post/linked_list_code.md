---
title: "連結リストの実装"
date: 2017-12-24T10:00:00+09:00
tags: [ "algorithm"]
---


```
class DoublyLinkedListNode(object):
    def __init__(self, value):
        self.value = value
        self.next = None
        self.prev = None


class SinglyLinkedListNode(object):
    def __init__(self, value):
        self.value = value
        self.next = None
```
