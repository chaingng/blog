
---
title: "[python] 画像ファイルのダウンロード"
date: 2020-08-10T10:00:00+09:00
tags: [ "python"]
---

この３行だけ。

```
from urllib import request
url = 'https://blogimg.goo.ne.jp/user_image/5e/22/e09e5f4d4d96832d380c6d87b5ee8fc6.jpg'
request.urlretrieve(url, "sample.jpg")
```

