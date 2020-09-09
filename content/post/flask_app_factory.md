---
title: "[flask] アプリケーションファクトリでFlaskを起動"
date: 2020-08-08T10:00:00+09:00
tags: [ "flask"]
---

Flask本体の起動について、これまでは直接グローバルでFlaskインスタンスを作成する方法が行われていたところ、問題を引き起こす可能性がありました。

そのため、関数内でFlaskインスタンスが作成する方法が追加されました。
これをアプリケーションファクトリと呼びます。

そして、アプリケーションファクトリを作成し、flaskコマンドにてアプリケーションを起動する方法がバージョン1.0にて追加されました。

今回こちらの方法を実行してみます。

- [１）flaskのインストール](#１flaskのインストール)
- [２）アプリケーションファクトリ関数を作成](#２アプリケーションファクトリ関数を作成)
- [３）環境変数を設定](#３環境変数を設定)
- [４）アプリケーションを起動](#４アプリケーションを起動)

## １）flaskのインストール

flaskがインストールされていなければ、pipでインストールします。

```
pip install Flask
```

## ２）アプリケーションファクトリ関数を作成

アプリケーションファクトリ関数を作成し、その中でFlaskインスタンスを作成します。

アプリケーション関数名は`create_app`もしくは`make_app`とすることで、Flask起動時に自動で読み込まれます。

具体的に、本体のソースコードの[こちら](https://github.com/pallets/flask/blob/1.0.x/flask/cli.py#L72)で自動で関数名を読み取りしています。


```
from flask import Flask

def create_app():
    app = Flask(__name__)

    @app.route('/')
    def hello():
        return 'Hello, World!'

    return app
```

## ３）環境変数を設定

ファクトリ関数が存在するモジュール名をFLASK_APP環境変数にて指定します。

今回アプリケーションファクトリ関数はhello.pyに存在するので、helloと指定します。

```
export FLASK_APP=hello 
```

## ４）アプリケーションを起動

最後に、flask runとすることでアプリケーションが起動します。

```
$ flask run
 * Serving Flask app "hello"
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: off
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
```
