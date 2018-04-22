---
title: "ソートの基礎"
date: 2018-01-15T10:00:00+09:00
tags: [ "algorithm"]
---

## overview
- ソートは検索を早くするプリプロセスとして使われる
- 似ているアイテムを探すのにも使われる
- ヒープソート
  - in-placeだが安定でない
  - spaceO(1)
- マージソート
  - 安定だがin-placeでない
  - space O(n)
  - avarage: O(n logn)
  - worst :O(n logn)
  - best: O(n logn)
- クイックソート
  - 最悪ケースでO(n^2)、安定でない
  - space O(n)
  - avarage: O(n logn)
  - worst :O(n^2)
  - best: O(n logn)
- max/min-heap
  - O(logn)で挿入・削除可能
  - O(1)でmin/maxの要素を参照できる
  
## bootcamp
生徒名とGPAを持つ生徒を並び替える

```
class Student(Object):
  def __init__(self, name, grade_point):
    self.name = name
    self.grade_point = grade_point
    
  def __lt__(self, other):
    return self.name < other.name
    
students = [
  Student('A', 4.0),
  Student('B', 3.0),
  Student('C', 3.2)
]

sorted(students)
students.sort(key=lambda student: student.grade_point)
```

## know libraries
- sort()
  - in-place
- sorted()
  - return new list

## 13.1 2つのソートされた配列の共通する要素のみからなる配列を返す

### brute force solution
- 全ての組み合わせを調べる
- O(mn)

### solution 2
-　binary searchで片方の配列を調べる
- O(mlogn) m:配列の長さ

### best solution
- 各配列を同時に左から順にみていき、比較していく
- O(m+n)
