---
title: "[python] スタックの実装"
date: 2018-02-23T10:00:00+09:00
tags: [ "python"]
---

## scratch

```

class AbstructStack:
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

class StackNode(object):
    def __init__(self, value):
        self.value = value
        self.next = None

class LinkedListStack(AbstructStack):
    def __init__(self):
        AbstructStack.__init__(self)
        self.front = 0

    def dequeue(self):
        if self.isEmpty():
            raise IndexError('stack is empty')
        value = self.front.value
        self.front = self.front.next
        self.top -= 1
        return value
    
    def enqueue(self, value):
        node = StackNode(value)
        if self.isEmpty():
            self.front = node
        else:
            node.next = self.front
            self.front = node
        self.top += 1
        return
    
    def peek(self):
        if self.isEmpty():
            raise IndexError('stack is empty')
        return self.front.value

    def __iter__(self):
        probe = self.front
        while True:
            if probe is None:
                raise StopIteration
            yield probe.value
            probe = probe.next

s = LinkedListStack()
s.enqueue(1)
s.enqueue(2)
s.enqueue(3)
s.dequeue()
print(s)
```

## pythonic

```
>>> stack = [3, 4, 5]
>>> stack.append(6)
>>> stack.append(7)
>>> stack
[3, 4, 5, 6, 7]
>>> stack.pop()
7
>>> stack
[3, 4, 5, 6]
>>> stack.pop()
6
>>> stack.pop()
5
>>> stack
[3, 4]
```
