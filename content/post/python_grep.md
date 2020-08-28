---
title: "[python] 文字列から条件付きで部分文字列を取得したい"
date: 2020-08-03T10:00:00+09:00
tags: [ "python"]
---

URL 'https://www.amazon.co.jp/gp/product/B07F2X9GRQ/ref=dbs_a_def_rwt_hsch_vapi_tkin_p1_i1' がある。

このうち、`/product/`の後の１０文字のコードを取得したい。

##  部分文字列の取得

1) `find()`メソッドで`/product/`の開始箇所を取得
2) その開始箇所からはじめて、部分文字列を取得

```
str = 'https://www.amazon.co.jp/gp/product/B07F2X9GRQ/ref=dbs_a_def_rwt_hsch_vapi_tkin_p1_i1'
idx = str.find('/product/')
print(str[idx+9:idx+19])
# 'B07F2X9GRQ'

# 9 == "/product/"の文字数
# 19 == "/product/"の文字数(9) + 取得したい文字の文字数(10)
```
