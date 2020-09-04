---
title: "[python] listをn個ずつ等分に分割"
date: 2020-08-07T10:00:00+09:00
tags: [ "python"]
---

[more-itertools](https://more-itertools.readthedocs.io/en/stable/)を使うことで、listをn個ずつ等分に分割することができる。


## more-itertools のインストール

```
pip install more-itertools
```

## listをn個ずつ等分に分割

```
from more_itertools import chunked

from more_itertools import chunked
l = [0, 1, 2, 3, 4, 5, 6, 7, 8]

list(chunked(l, 2))
# [[0, 1], [2, 3], [4, 5], [6, 7], [8]]

list(chunked(l, 3))
# [[0, 1, 2], [3, 4, 5], [6, 7, 8]]
```
