---
title: "[python] listをタブ区切り/スペース区切りで表示させる"
date: 2020-08-25T10:00:00+09:00
tags: [ "python"]
---

## タブ区切りで表示

```
>>> l = ['a', 'b', 'c', 'd', 'e']
>>> print('\t'.join([str(i) for i in l]))
a	b	c	d	e
```

## スペース区切りで表示

```
>>> l = ['a', 'b', 'c', 'd', 'e']
>>> print(' '.join([str(i) for i in l]))
a b c d e
```

## コンマ区切りで表示

```
>>> l = ['a', 'b', 'c', 'd', 'e']
>>> print(','.join([str(i) for i in l]))
a,b,c,d,e
```

## 改行して表示

```
>>> l = ['a', 'b', 'c', 'd', 'e']
>>> print('\n'.join([str(i) for i in l]))
a
b
c
d
e
```
