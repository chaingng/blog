---
title: "pythonの比較におけるisと==の違い"
date: 2018-01-30T10:00:00+09:00
tags: [ "python"]
---

[reference](https://docs.python.jp/3/reference/expressions.html#comparisons)によると、以下の通り。
- `==`はオブジェクトの値が同一か比較する。基本はこちらを使う。
- `is`は同じオブジェクトがどうか比較する。比較にはid()の値を使う。


## 例
string
```
>>> s1 = 'hoge'
>>> s2 = 'hoge'
>>> id(s1)
4379138456
>>> id(s2)
4379138456
>>> s1 == s2
True
>>> s1 is s2
True
```

list
```
>>> l1= []
>>> l2= []
>>> id(l1)
4379117128
>>> id(l2)
4378993608
>>> l1 == l2
True
>>> l1 is l2
False
```

tuple
```
>>> t1=(3,3)
>>> t2=(3,3)
>>> id(t1)
4379077832
>>> id(t2)
4379078472
>>> t1 == t2
True
>>> t1 is t2
False
```
