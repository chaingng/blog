---
title: "pythonデータ型ごとのビット数"
date: 2018-01-15T10:00:00+09:00
tags: [ "python"]
---

## int
intはデフォルトで28bit
```
>>> import sys
>>> sys.getsizeof(1)
28
```

超えると自動で拡張される
```
>>> sys.getsizeof(1<<32)
32
>>> sys.getsizeof(1<<60)
36
>>> sys.getsizeof(1 << 10000)
1360
```

## 浮動小数
デフォルトで24bit
```
>>> sys.getsizeof(0.1)
24
## 増やしても変わらない様子
>>> sys.getsizeof(111111111.11111111)
24
```

## string
デフォルトで50bit
```
>>> sys.getsizeof(u'a')
50
# 長さに応じて増えていく
>>> sys.getsizeof(u'ab')
51
```

## list
デフォルトで64bit
```
>>> sys.getsizeof(list())
64

# 長さに応じて増えていく
>>> sys.getsizeof([1])
72
>>> sys.getsizeof([1,1])
80
>>> sys.getsizeof([1, 1, 1])
88
```

## その他
```
>>> sys.getsizeof(tuple())
48
>>> sys.getsizeof(dict())
240
>>> sys.getsizeof(set())
224
```
