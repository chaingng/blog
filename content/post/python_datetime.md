---
title: "[python] 現在時刻を扱う"
date: 2020-08-05T10:00:00+09:00
tags: [ "python"]
---

Pythonの標準モジュール`datetime`を使うと、日付や時間を操作できるようになる。　

## 現在の時刻を取得

```
>>> from datetime import datetime
>>> datetime.now()
datetime.datetime(2020, 8, 25, 14, 4, 6, 131518)

```

## 文字列を時刻に変換

```
>>> prev_time = '2020.08.01 14:02:10'
>>> datetime.strptime(prev_time, '%Y.%m.%d %H:%M:%S')
datetime.datetime(2020, 8, 1, 14, 2, 10)
```

## 現在の時刻との差を計算

「`-`」 をすることで差を計算することができる

```
>>> current_datetime = datetime.now()
>>> prev_datetime = datetime.strptime(prev_time, '%Y.%m.%d %H:%M:%S')
>>> current_datetime - prev_datetime
datetime.timedelta(days=24, seconds=301, microseconds=671860)
```

差は、「日数(days) + 秒数(seconds) + マイクロ秒数(microseconds)の和」で表される

### 日数単位で差を取得したい時

```
>>> (current_datetime - prev_datetime).days
24
```

### 秒数単位で差を取得したいとき

```
>>> (current_datetime - prev_datetime).seconds +  (current_datetime - prev_datetime).days * 3600*24
2073901
```
