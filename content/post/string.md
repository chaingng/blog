---
title: "文字列の基礎"
date: 2017-11-26T10:00:00+09:00
tags: [ "algorithm"]
---

## 概要
- 比較、コピー、連結、分割、マッチなど基本操作について理解する
- brute-forceではO(n)spaceだが、ソリューションによってはO(1)spaceに減ることもできる
- python stringはimmutableであることを理解する
- mutableな処理には代わりにlistを使う
- 後ろから処理することが有効なこともある

## 回文かのチェック

```
def is_pelindromic(s):
  return all( s[i] == s[~i] for i in range(len(s)//2) )
```

## 6.1 文字列を数字に変換

### brute-force
- 右から見ていき、次に足す数字に対して10ずつかける回数を増やしていく

### best solution
- 左から見ていき、これまでの値に10をかけて次の値を足していく

```
def string_to_int(s):
    num = 0
    if s[0] == '-':
        start = 1
        nagative = True
    else:
        start = 0
        nagative = False

    for i in range(start, len(s)):
        num = num * 10 + int(s[i])
    return num * -1 if nagative else num
    
print(string_to_int('314'))
print(string_to_int('-14314'))    
```
