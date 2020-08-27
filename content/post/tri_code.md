---
title: "[python] トライ木の実装"
date: 2018-03-23T10:00:00+09:00
tags: [ "python"]
---


```
import collections

class TriNode(object):
    def __init__(self):
        self.children = collections.defaultdict(TriNode)
        self.is_word = False

class TriTree:
    def __init__(self):
        self.root = TriNode()
    
    def insert(self, word):
        current = self.root
        for letter in word:
            current = current.children[letter]
        current.is_word = True        


    def search(self, word):
        current = self.root
        for letter in word:
            current = current.children[letter]
            if current is None:
                return False
        return current.is_word

    def startswith(self, prefix):
        current = self.root
        for letter in prefix:
            current = current.children[letter]
            if current is None:
                return False
        return True

t = TriTree()
t.insert('hoge')
t.insert('fuga')
print(t.search('hoge'))
print(t.search('ho'))
print(t.search('hogefuga'))
```
