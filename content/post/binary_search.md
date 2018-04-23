---
title: "二分探索の基礎と実装"
date: 2017-12-03T10:00:00+09:00
tags: [ "algorithm"]
---

## 概要
- sorting O(nlogn)
- search O(logn)
- `mid = (low + high)/2` はオーバーフローしてしまう
- `mid = low + (high - low)/2`ならよい

## 実装

```
def bsearch(t,A):
  low, high = 0, len(A)-1
  while low <= high:
    mid = (low + high)//2
    if A[mid] < t:
      low = mid + 1
    else if A[mid] == t:
      return mid
    else:
      high = mid - 1
  return -1
```

## 11.1 ソート済み配列から最初にKが現れる場所を探す
- kは複数存在しうるので、そのうちの一番最初の場所を返してあげる必要がある


### naive approach
- Kが見つかったら、バックトラックする
- worst O(n) time

### best solution
- ｋに一致するときの条件を加えた二分探索
- log(n)

```
def search_first_of_k(A, k):
  left, right, result = 0, len(A)-1, -1
  while left <= right:
    mid = (left + right) // 2
    if A[mid] > k:
      right = mid - 1
    else if A[mid] < k:
      left = mid + 1
    else:
      result = mid
      right = mid - 1

  return result
```
