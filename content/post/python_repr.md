---
title: "[python]__repr__と__str__の違い"
date: 2018-01-22T10:00:00+09:00
tags: [ "python"]
---

[Reference](https://docs.python.jp/3/reference/datamodel.html)によると以下の通り。

## `__str__(self)`
- オブジェクトの「非公式の (informal)」あるいは表示に適した文字列表現を計算するために呼ばれる
- str(object) と組み込み関数 format(), print() によって呼ばれる

## `__repr__(self)`
- オブジェクトを表す「公式の (official)」文字列を計算するために呼ばれる
- repr()によって呼び出される
- `__repr__()` を定義していて `__str__()` は定義していなければ、__str__が呼び出されるべき関数も__repr__が呼ばれる

## 例
```
class Item(object):
    def __init__(self, obj, key):
        self.obj = obj
        self.key = key

    def __repr__(self):
        return 'repr: '+ str(self.obj) + ': ' + str(self.key)

    def __str__(self):
        return 'str : ' + str(self.obj) + ': ' + str(self.key)


item = Item('a', 5)

print(item)
>> str : a: 5

print(repr(item))
>> repr: a: 5
```


