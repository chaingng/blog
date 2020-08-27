---
title: "[python] キューの実装"
date: 2018-02-23T10:00:00+09:00
tags: [ "python"]
---

## scratch

```
# queueのベースクラスを作成 
# isEmpty, lenメソッド, 全nodeの一覧を持つ
class AbstractQueue:
    def __init__(self):
        self.top = 0

    def isEmpty(self):
        return self.top == 0

    def __len__(self):
        return self.top

    def __str__(self):
        result = '------\n'
        for element in self:
            result += str(element) + '\n'
        return result[:-1] + '\n------' 

# nodeクラスを作成　
# 値：value, nextを持つ
class QueueNode(object):
    def __init__(self, value):
        self.value = value
        self.next = None

# queueクラスを実装
# 値：front, rearをもつ
# メソッド：enqueue, dequeue, isEmptyを持つ
# iter可能
class LinkedListQueue(AbstractQueue):
    def __init__(self):
        AbstractQueue.__init__(self)
        self.front = None
        self.rear = None

    # enqueue
    # rearに値を追加する
    def enqueue(self, value):
        node = QueueNode(value)
        if not self.front:
            self.front = node
            self.rear = node
        else:
            self.rear.next = node
            self.rear = node
        self.top += 1

    # dequeue
    # frontの値を削除する
    def dequeue(self):
        if self.isEmpty():
            raise IndexError('queue is empty')
        value = self.front.value
        if self.front is self.rear:
            self.front = None
            self.rear = None
        else:
            self.front = self.front.next
        self.top -= 1
        return value

    # __iter__を実装
    def __iter__(self):
        probe = self.front
        while True:
            if probe is None:
                raise StopIteration
            yield probe.value
            probe = probe.next


q = LinkedListQueue()
q.enqueue(1)
q.enqueue(2)
q.enqueue(3)
q.dequeue()
print(str(q))

```

## pythonic

```
>>> from collections import deque
>>> queue = deque(["Eric", "John", "Michael"])
>>> queue.append("Terry")           # Terry arrives
>>> queue.append("Graham")          # Graham arrives
>>> queue.popleft()                 # The first to arrive now leaves
'Eric'
>>> queue.popleft()                 # The second to arrive now leaves
'John'
>>> queue                           # Remaining queue in order of arrival
deque(['Michael', 'Terry', 'Graham'])
```
