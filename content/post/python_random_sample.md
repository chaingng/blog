
---
title: "[python] listからランダムに要素を選択する"
date: 2020-08-06T10:00:00+09:00
tags: [ "python"]
---

`random.sample()`を使うことで、リストから指定した要素分、ランダムに要素を選択することができる。

```
import random
l = [0, 1, 2, 3, 4, 5]

random.sample(l, 3)
# [4, 0, 5]

random.sample(l, 3)
# [2, 3, 1]
```
