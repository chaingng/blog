---
title: "[python] classの使い方"
date: 2020-07-01T00:00:00+09:00
tags: [ "python"]
---



classについて、たくさんあるが最小限の使い方についてメモ。

## 使い方

- `__init__`でインスタンス作成時のオペレーションを定義する
- インスタンスメソッドの定義では、第一引数は(self, xxx)と必ず`self`にする
- `インスタンス.変数名`でインスタンス変数が参照できる
- `インスタンス.インスタンスメソッド`でインスタンスメソッドを実行

## サンプルコード

限りなくミニマムなコード 

```
class Person:
    def __init__(self, family_name, first_name):
        self.family_name = family_name
        self.first_name = first_name

    def get_full_name(self):
        return '{} {}'.format(self.family_name, self.first_name)
    

person = Person('田中', '一郎')
print('名字:', person.family_name)
print('フルネーム:', person.get_full_name())
```
