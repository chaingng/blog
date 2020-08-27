---
title: "[python] マージソートの実装"
date: 2018-02-09T10:00:00+09:00
tags: [ "python"]
---

```
# https://ja.wikipedia.org/wiki/%E3%83%9E%E3%83%BC%E3%82%B8%E3%82%BD%E3%83%BC%E3%83%88
# http://www.ics.kagoshima-u.ac.jp/~fuchida/edu/algorithm/sort-algorithm/merge-sort.html


def merge_sort(array):
    # 配列の長さが１ならソート不要なので返す
    if len(array) <= 1:
        return array

    # それより長いなら半分に分割してそれぞれにマージソートを適用する
    mid = len(array) // 2
    left = merge_sort(array[:mid])
    right = merge_sort(array[mid:])

    # 半分に分割した左と右について統合を行う
    return merge_array(left, right)


def merge_array(left, right):
    array = []
    left_idx = 0
    right_idx = 0
    while left_idx < len(left) and right_idx < len(right):
        if left[left_idx] < right[right_idx]:
            array.append(left[left_idx])
            left_idx += 1
        else:
            array.append(right[right_idx])
            right_idx += 1

    if left_idx < len(left):
        array.extend(left[left_idx:])
    if right_idx < len(right):
        array.extend(right[right_idx:])

    return array


array = [1, 5, 65, 23, 57, 1232, -1, -5, -2, 242, 100,
         4, 423, 2, 564, 9, 0, 10, 43, 64, 32, 1, 999]
print(array)
print(merge_sort(array))

```
