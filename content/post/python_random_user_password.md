---
title: "[python] ユーザ用にランダムな英数字パスワードを生成する"
date: 2018-01-01T10:00:00+09:00
tags: [ "python"]
---

## 英数字8文字のランダムパスワードを生成

```
>>> import random, string
>>> ''.join([random.choice(string.ascii_letters + string.digits) for i in range(8)])
'8GkJXlpr'
```

数字だけの場合は`string.digits`のみにし、長さを変更したい場合は`8`のところを変更すればよい。
