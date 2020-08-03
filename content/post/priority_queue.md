---
title: "Pythonでの優先度付きキューの実装"
date: 2018-03-16T10:00:00+09:00
tags: [ "python"]
---

```
import sys

class PriorityQueueNode(object):
    def __init__(self, obj, key):
        self.obj = obj
        self.key = key

    def __repr__(self):
        return str(self.obj) + ': ' + str(self.key)

class PriorityQueue(object):
    def __init__(self):
        self.array = []

    # 要素を追加
    def insert(self, node):
        self.array.append(node)
        return self.array[-1]

    # 最も高い優先度のnodeを取り出し
    def extract_min(self):
        if self.array is None:
            return None
        minimum = sys.maxsize
        minimum_index = -1
        for i in range(len(self.array)):
            if self.array[i].key < minimum:
                minimum = self.array[i].key
                minimum_index = i
        return self.array.pop(minimum_index) 

    # objの優先度を変更
    def decrease_key(self, obj, new_key):
        for node in self.array:
            if node.obj == obj:
                node.key = new_key
                return node
        return None

priority_queue = PriorityQueue()
print(priority_queue.insert(PriorityQueueNode('a', 20)))
print(priority_queue.insert(PriorityQueueNode('b', 5)))
print(priority_queue.insert(PriorityQueueNode('c', 15)))
mins = []
while priority_queue.array:
    mins.append(priority_queue.extract_min().key)

print(mins)

```
