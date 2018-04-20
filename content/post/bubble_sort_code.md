---
title: "バブルソートの実装"
date: 2018-02-12T10:00:00+09:00
tags: [ "algorithm"]
---

```
# https://ja.wikipedia.org/wiki/%E3%83%90%E3%83%96%E3%83%AB%E3%82%BD%E3%83%BC%E3%83%88
# 交換を最大 n-1 , n-2, ... 1回 = n(n-1)/2 回 ->  O(n^2)

def bubble_sort(array):
    # 最初は0からn-1まで探索し一番大きい要素をn-1に
    # 次は0からn-2まで一番大きい要素をn-2に
    # 交換が発生しなければ終了
    # 0から0になれば終了
    for i in reversed(range(0, len(array))):
        swapped = False
        for j in range(0, i):
            if array[j] > array[j+1]:
                array[j], array[j+1] = array[j+1], array[j]
                swapped = True
        if not swapped:
            break

array = [1, 5, 65, 23, 57, 1232, -1, -5, -2, 242, 100,
         4, 423, 2, 564, 9, 0, 10, 43, 64, 32, 1, 999]
print(array)
bubble_sort(array)
print(array)
```
