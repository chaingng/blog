---
title: "Pythonでのハッシュテーブルの実装"
date: 2018-03-09T10:00:00+09:00
tags: [ ""]
---



```
class Item(object):
    def __init__(self, key, value):
        self.key = key
        self.value = value

class HashTable(object):
    def __init__(self, size=10):
        self.size = size
        self.array = [[] for _ in range(self.size)]

    def _hash_function(self, key):
        return key % self.size

    def set(self, key, value):
        hash_index = self._hash_function(key)
        for node in self.array[hash_index]:
            if node.key == key:
                node.value = value
                return
        self.array[hash_index].append(Item(key, value))
    
    def get(self, key):
        hash_index = self._hash_function(key)
        for node in self.array[hash_index]:
            if node.key == key:
                return node.value
        raise KeyError('key not found')

    def remove(self, key):
        hash_index = self._hash_function(key)
        for index, item in enumerate(self.array[hash_index]):
            if item.key == key:
                del self.array[hash_index][index]
                return
        raise KeyError('key not found')

hash_table = HashTable(10)
hash_table.set(0, 'foo')
print(hash_table.get(0))
hash_table.set(1, 'bar')
hash_table.remove(0)
```
