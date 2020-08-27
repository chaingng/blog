---
title: "[python] python2ではtimestamp()が使えないのでdatetimeに変換して日付を比較する"
date: 2018-01-02T10:00:00+09:00
tags: [ "python"]
---

python3ではdatetimeをタイム・スタンプに変換する`timestamp()`が使えるが、python2では存在しない。
そこで、日付の比較をするには、タイプスタンプ側をdatetimeに変換して比較する。

## ファイルが7日以上前に作られたかどうか判定するコード

```
import os
import datetime

def after_7_days(localfile):
  ctime = os.path.getctime(localfile)
  current_time = datetime.datetime.now() - datetime.timedelta(days=7)
  return datetime.datetime.fromtimestamp(ctime) < current_time

after_7_days('/Users/hondatakatomo/hoge.log')
```
