---
title: "Python dot-envの使い方"
date: 2017-08-01T00:00:00+09:00
tags: [ "python"]
---

python-dotenvを使うことで、`.env`ファイルを使って環境変数を扱うことができる。

これだけの手順でよい。

1. `python-dotenv`をインストール
1. `.env`ファイルを作成
1. `settings.py`を作成
1. `settings`をインポートして実行

最小限のコードは以下のとおり。

## 1) インストール

```
pip install python-dotenv
```

## 2) .envファイルを作成

.env
```
API_KEY=ITSMYAPIKEY
```

## 3) settings.pyを作成

settings.py
```
import os
from os.path import join, dirname
from dotenv import load_dotenv

dotenv_path = join(dirname(__file__), '.env')
load_dotenv(dotenv_path)

AP= os.environ.get("API_KEY")
```

## 4) settingsをインポートして実行

sample.py
```
import settings

API_KEY = settings.AP
print(API_KEY)
```
