---
title: "[python] jpg画像をpng画像に変換"
date: 2020-08-27T10:00:00+09:00
tags: [ "python"]
---

## pillowライブラリのインストール

`pillow`はPythonにおける画像ライブラリ。

`pillow`ライブラリを使用することで、様々な画像処理を行うことが可能。

```
pip install pillow
```

## jpg画像をpng画像に変換

```
from PIL import Image
im = Image.open('after.jpg')
im.save('after.png')
```

