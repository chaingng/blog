---
title: "[python] クイックソートの実装"
date: 2018-02-16T10:00:00+09:00
tags: [ "python"]
---

```
# https://ja.wikipedia.org/wiki/%E3%82%AF%E3%82%A4%E3%83%83%E3%82%AF%E3%82%BD%E3%83%BC%E3%83%88
# http://www.ics.kagoshima-u.ac.jp/~fuchida/edu/algorithm/sort-algorithm/quick-sort.html


def quick_sort(array, first, last):
    # あるpivotをもとに、そこから左だけはpivot以下の値だけに、右はpivot以上の値だけにする
    #　左と右の配列に対してquicksortを再帰的に適用する
    if first < last:
        pivot = partition(array, first, last)
        quick_sort(array, first, pivot - 1)
        quick_sort(array, pivot + 1, last)


def partition(array, first, last):
    # あるpivotをもとに、そこから左だけはpivot以下の値だけに、右はpivot以上の値だけにする
    # lastの値をpivotとし、それ以下の値を左にくるようにする
    pivot = first
    for i in range(first, last):
        if array[i] < array[last]:
            array[i], array[pivot] = array[pivot], array[i]
            pivot += 1
    array[last], array[pivot] = array[pivot], array[last]

    return pivot


array = [1, 5, 65, 23, 57, 1232, -1, -5, -2, 242, 100,
         4, 423, 2, 564, 9, 0, 10, 43, 64, 32, 1, 999]
print(array)
quick_sort(array, 0, len(array) - 1)
print(array)

```
