---
title: "[python] ファイルの読み書きまとめ"
date: 2020-08-26T10:00:00+09:00
tags: [ "python"]
---

## 目次
- [ファイルの書き込み](#ファイルの書き込み)
- [ファイルの読み込み](#ファイルの読み込み)
- [ファイルのデフォルト読み込み](#ファイルのデフォルト読み込み)
- [ファイルの追加書き込み](#ファイルの追加書き込み)
- [ファイルを１行ずつ読み込み](#ファイルを１行ずつ読み込み)
- [ファイルをリストとして読み込み](#ファイルをリストとして読み込み)

## ファイルの書き込み

モードに`'w'`を指定する。

```
with open('sample.txt', 'w') as f:
    f.write('Hello, world!\n')
```

## ファイルの読み込み

モードに`'r'`を指定する。

```
with open('sample.txt', 'r') as f:
    data = f.read()

print(data)
# 'Hello, world!'
```

## ファイルのデフォルト読み込み

モードは指定しなければ'r'となる。
そのため、読み込み時はモードの指定は不要。

```
with open('sample.txt') as f:
    data = f.read()

print(data)
# 'Hello, world!'
```

## ファイルの追加書き込み

モードに'a'を指定する。

```
with open('sample.txt', 'a') as f:
    f.write('Hello, again!')
```

追加書き込みがされていることが確認できる。

```
with open('sample.txt') as f:
    data = f.read()

print(data)
# Hello, world!
# Hello, again!
```

## ファイルを１行ずつ読み込み

```
with open('sample.txt') as f:
    for line in f:
        print(line)
# Hello, world!
# 
# Hello, again!        
```

## ファイルをリストとして読み込み

```
with open('sample.txt') as f:
    l = [s.strip() for s in f.readlines()]

print(l)
# ['Hello, world!', 'Hello, again!']
```
