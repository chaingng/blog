---
title: "配列の基礎"
date: 2017-11-19T10:00:00+09:00
tags: [ "algorithm"]
---

## 概要
- データの取得と更新がO(1)
- 削除がO(n-i)
- 時々resizingが必要になる
- brute forceでO(n)spaceだが、ソリューションによってはO(1)space
- 後ろから探索することが有効な時がある
- 削除に変わって、オーバーライドが有効なこともある
- 後ろから数字を扱うのが有効な時がある
- 二次元配列には並行処理が有効な場合もある
- シミュレーションするとソリューションが浮かびやすいこともある

## 5.1 Dutch flag problem
- 数字の配列を、与えられたpivot以下、pivotと同じ値、pivotより大きい値に並べる

```
def dutch_flag(pivot_index, A):
    pivot = A[pivot_index]
    smaller, equal, larger = 0, 0, len(A)

    while equal < larger:
        if A[equal] < pivot:
            A[smaller], A[equal] = A[equal], A[smaller]
            smaller, equal = smaller + 1, equal + 1
        elif A[equal] == pivot:
            equal += 1
        else:
            larger -= 1
            A[equal], A[larger] = A[larger], A[equal]
    return A


ret = dutch_flag(1, [4, 0, -1, 1, -1, 1, 0, 2])
print(ret)
```
