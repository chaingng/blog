---
title: "Blueprintでflaskアプリケーションをわかりやすく構造化する"
date: 2018-01-08T10:00:00+09:00
tags: [ "flask"]
---

[blueprint](http://exploreflask.com/en/latest/blueprints.html)を使うことで、flaskアプリケーションをわかりやすく構造化することができる。


## まとめ
* ブループリントはアプリケーションを構造化するのに役に立つ
* ブループリントを使うと、ビュー、テンプレート、staticfilesをまとめてアプリケーションに適用できる
* プラクティスとして、divisionalな構造化またはfunctionalな構造化がある
* divisionalな構造では、各ブループリントはビュー、テンプレート、staticfileをまとめてアプリケーションの１つのセクションにする
* functionalな構造では、各ブループリントは単なるビューの集まりにする。テンプレートとstaticfileは共通のままにしておく
* url_value_preprocessor()を使うことで、viewに渡す前の前処理を追加できる
* url prefixを適用できる
* サブドメインを適用できる


## 基本的な使い方

blueprintに追加したいビューにて、blueprintを作成する。

ここでは、profileという名前でblueprintを作成する

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

flaskアプリケション側で、profileという名前で定義したblueprintを登録する。

```
# facebook/__init__.py

from flask import Flask
from .views.profile import profile

app = Flask(__name__)
app.register_blueprint(profile)
```

## URL prefixを追加

ビュー側、もしくはアプリケーション側のいずれかでurl_prefixを定義することでルーティングにURL Prefixを追加できる。

### ビュー側で定義する場合

```
# facebook/views/profile.py

from flask import Blueprint, render_template

profile = Blueprint('profile', __name__, url_prefix='/<user_url_slug>')

# [...]
```

### アプリケーション側で定義する場合

```
# facebook/__init__.py

from flask import Flask
from .views.profile import profile

app = Flask(__name__)
app.register_blueprint(profile, url_prefix='/<user_url_slug>')
```

## サブドメインを追加

ルーティングにサブドメインを追加することもできる。

ビュー側、もしくはアプリケーション側で定義する。

### ビュー側で追加する場合

```
# sitemaker/__init__.py

from flask import Flask
from .site import site

app = Flask(__name__)
app.register_blueprint(site, subdomain='<site_subdomain>')
```

### アプリケーション側で追加する場合

```
# facebook/__init__.py

from flask import Flask
from .views.profile import profile

app = Flask(__name__)
app.register_blueprint(profile, url_prefix='/<user_url_slug>')
```


## viewに渡す前の前処理を追加

url_value_preprocessor()を使うことで、viewに渡す前の前処理を記述することができる


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

gはJinja2のコンテキスト。これに渡すとビューで参照できる


## blueprintを使った構造化のtips。divisionalな構造化かfunctionalな構造化か？

blueprintを使ったアプリケーションの構造化にはプラクティスとして２つの観点がある。

アプリケーションの特性に合わせて、いずれかを参考にするとよい。


### divisionalな構造化

ビュー、テンプレート、staticfileをまとめてアプリケーションの１つのセクションにする方法。

テンプレートやstaticfileを共有しておらず、blueprintにまとめたい部分の独立性が高い場合はこちらの方法をとる。


### functionalな構造化

ビューのみをblueprintに登録する方法。

テンプレートに共通のレイアウトファイルがあったりstaticfileに共有するものが多い場合は、テンプレートとstaticfileは変わらず共通のままにして、ビューファイルのみblueprintに登録する。
