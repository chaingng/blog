---
title: "[flask] Blueprintを用いたアプリケーションの分割とベストプラクティス"
date: 2018-01-08T10:00:00+09:00
tags: ["flask"]
---

## Blueprintとは

[Blueprint](https://flask.palletsprojects.com/en/1.1.x/tutorial/views/)とは、アプリケーションを分割するための機能です。

Blueprintを使うことで、関連するビューやコードを一つにまとめて、独立して扱うことが可能になります。

大規模なアプリケーションを開発する場合は、Blueprintを使うことが推奨されています。

## 目次
- [まとめ](#まとめ)
- [基本的な使い方](#基本的な使い方)
- [追加の設定](#追加の設定)
  - [url_prefixを追加する](#url_prefixを追加する)
  - [サブドメインを追加する](#サブドメインを追加する)
  - [viewに渡す前の前処理を追加する](#viewに渡す前の前処理を追加する)
- [Blueprintにおける２つのベストプラクティス](#Blueprintにおける２つのベストプラクティス)

## まとめ
* ブループリントによってアプリケーションの構造化が可能
* ブループリントを使うと、ビュー・テンプレート・staticfileを１つにまとめ、アプリケーションに適用することが可能
* ベストプラクティスとして、divisionalな構造化またはfunctionalな構造化がある
  * divisionalな構造では、各ブループリントはビュー、テンプレート、staticfileをまとめてアプリケーションの１つのセクションにする
  * functionalな構造では、各ブループリントは単なるビューの集まりにする。テンプレートとstaticfileは共通のままにしておく
* 追加の設定
  * url_value_preprocessor()を使うことで、viewに渡す前の前処理を追加できる
  * url prefixを適用することができる
  * サブドメインを適用することができる


## 基本的な使い方

Blueprintに追加したいビューにて、Blueprintを作成する。

ここでは、`profile`という名前でBlueprintを作成

```
# facebook/views/profile.py

from flask import Blueprint, render_template

profile = Blueprint('profile', __name__)

@profile.route('/<user_url_slug>')
def timeline(user_url_slug):
    # Do some stuff
    return render_template('profile/timeline.html')

@profile.route('/<user_url_slug>/photos')
def photos(user_url_slug):
    # Do some stuff
    return render_template('profile/photos.html')

@profile.route('/<user_url_slug>/about')
def about(user_url_slug):
    # Do some stuff
    return render_template('profile/about.html')
```

flaskアプリケーション側で`profile`という名前でBlueprintに登録

```
# facebook/__init__.py

from flask import Flask
from .views.profile import profile

app = Flask(__name__)
app.register_blueprint(profile)
```

## 追加の設定

### url_prefixを追加する

url_prefixを定義することでルーティングにURL Prefixを追加できる。

#### ビュー側で定義する場合

```
# facebook/views/profile.py

from flask import Blueprint, render_template

profile = Blueprint('profile', __name__, url_prefix='/<user_url_slug>')
```

#### アプリケーション側で定義する場合

```
# facebook/__init__.py

from flask import Flask
from .views.profile import profile

app = Flask(__name__)
app.register_blueprint(profile, url_prefix='/<user_url_slug>')
```

### サブドメインを追加する

ルーティングにサブドメインを追加することも可能。

#### ビュー側で追加する場合

```
# sitemaker/__init__.py

from flask import Flask
from .site import site

app = Flask(__name__)
app.register_blueprint(site, subdomain='<site_subdomain>')
```

#### アプリケーション側で追加する場合

```
# facebook/__init__.py

from flask import Flask
from .views.profile import profile

app = Flask(__name__)
app.register_blueprint(profile, url_prefix='/<user_url_slug>')
```


### viewに渡す前の前処理を追加する

`url_value_preprocessor()`を使うことで、viewに渡す前の前処理を追加することが可能。

`g`はJinja2のコンテキスト。これに渡すとビューで参照できる。

```
# facebook/views/profile.py

from flask import Blueprint, render_template, g

from ..models import User

# The prefix is defined on registration in facebook/__init__.py.
profile = Blueprint('profile', __name__)

@profile.url_value_preprocessor
def get_profile_owner(endpoint, values):
    query = User.query.filter_by(url_slug=values.pop('user_url_slug'))
    g.profile_owner = query.first_or_404()

@profile.route('/')
def timeline():
    return render_template('profile/timeline.html')

@profile.route('/photos')
def photos():
    return render_template('profile/photos.html')

@profile.route('/about')
def about():
    return render_template('profile/about.html')
```


## Blueprintにおける２つのベストプラクティス

blueprintを使ったアプリケーションの構造化にはプラクティスとして２つの観点がある。

アプリケーションの特性に合わせて、いずれかを選択するとよい。


### divisionalな構造化

- ビュー、テンプレート、staticfileをまとめてアプリケーションの１つのセクションにする方法。
- テンプレートやstaticfileを共有しておらず、blueprintにまとめたい部分の独立性が高い場合はこちらの方法をとる。

divisionalな構造にする場合は、以下のような構成になる。

```
yourapp/
    __init__.py
    admin/
        __init__.py
        views.py
        static/
        templates/
    home/
        __init__.py
        views.py
        static/
        templates/
    control_panel/
        __init__.py
        views.py
        static/
        templates/
    models.py
```

### functionalな構造化

- ビューのみをblueprintに登録する方法。
- テンプレートに共通のレイアウトファイルがあったりstaticfileに共有するものが多い場合は、テンプレートとstaticfileは変わらず共通のままにして、ビューファイルのみblueprintに登録する。

functionalな構造にする場合は、以下のような構成になる。

```
yourapp/
    __init__.py
    static/
    templates/
        home/
        control_panel/
        admin/
    views/
        __init__.py
        home.py
        control_panel.py
        admin.py
    models.py
```
