---
title: "csrf対策"
date: 2018-01-24T10:00:00+09:00
tags: [ "django"]
---

## CSRFとは
Cross Site Request Forgeryの略。

ユーザーがWebアプリケーションにログインすると、CookieにSessionIDがセットされる。  
その状態で、悪意のあるサイトにアクセスしSessionIDを送信させる。  
そして入手したSessionIDを利用しWebアプリケーションに悪意のあるアクセスを行うことで、Webアプリケーションは正常なアクセスと判断し、結果としてユーザー情報が盗まれたり情報が改ざんされてしまう。

## Djangoでの対策
[Django](http://docs.djangoproject.jp/en/latest/ref/contrib/csrf.html)ではform送信時にhiddenパラメータにてトークンを埋め込み、送信されたリクエストに対しサーバ側でトークンを検証することでCSRFを防ぐことができる。

### クライアント
クライアント側では、フォームに`{% csrf_token %}`と記載しトークンを埋め込む。
```
<form action="." method="post">{% csrf_token %}
```

### サーバ
サーバ側のviewでは以下２つのいずれかを実装する。

1.RequestContext を使用

RequestContext は、(TEMPLATE_CONTEXT_PROCESSORS の設定によらず) 'django.core.context_processors.csrf' を常に使用する。

[renderメソッド](http://docs.djangoproject.jp/en/latest/topics/http/shortcuts.html)はデフォルトでRequestContext インスタンスを利用するので、
renderメソッドをそのまま利用するだけでよい。

```
def my_view(request):
    return render(request, 'grade.html', {'form’:form })
```

2.手動でインポートし、プロセッサーを使って CSRF トークンを生成して、 テンプレートのコンテキストに追加する
```
from django.core.context_processors import csrf
from django.shortcuts import render_to_response

def my_view(request):
    c = {}
    c.update(csrf(request))
    # ... view code here
    return render_to_response("a_template.html", c)
```
