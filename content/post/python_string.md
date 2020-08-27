---
title: "[python] string文字列の使い方"
date: 2017-04-30T10:00:00+09:00
tags: [ "python"]
---

### 連続して並んでいる文字を連結する
```
>>> 'Py' 'thon'
'Python'
```

### 負のindexを指定
```
>>> word = 'Python'
>>> word[-1]  # last character
'n'
>>> word[-2]  # second-last character
'o'
>>> word[-6]
'P'
```

### スライス
```
>>> word[:2]   # character from the beginning to position 2 (excluded)
'Py'
>>> word[4:]   # characters from position 4 (included) to the end
'on'
>>> word[-2:]  # characters from the second-last (included) to the end
'on'
```

### 大きすぎるindexを指定するとエラー
```
>>> word[42]  # the word only has 6 characters
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: string index out of range
```

### 大きすぎるスライスを指定した際はエラーにならない
```
>>> word[4:42]
'on'
>>> word[42:]
''
```

### 文字列は不変(immutable)
```
>>> word[0] = 'J'
  ...
TypeError: 'str' object does not support item assignment
>>> word[2:] = 'py'
  ...
TypeError: 'str' object does not support item assignment
```

