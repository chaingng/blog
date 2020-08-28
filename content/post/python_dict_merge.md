---
title: "[python] dictのマージ"
date: 2020-08-04T10:00:00+09:00
tags: [ "python"]
---

`update()`でdictをマージすることができる。

```
d1 = {'a':1 , 'b':2}
d2 = {'c':3 , 'd':4}
d1.update(d2)
print(d1)
# {'a': 1, 'b': 2, 'c': 3, 'd': 4}
```
