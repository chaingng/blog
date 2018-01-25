---
title: "djangoでのloggerの使い方"
date: 2018-01-25T10:00:00+09:00
tags: [ "django"]
---

djangoでloggerを使うには、loggerの要素（formatters、loggers、filters、handlers）とログレベル、settingsにおける設定について理解する必要がある。


## ログレベル

ログはレベルをもつ。指定したログレベル以下では操作させない、といった設定ができる

低位のレベルから以下のログレベルが存在する
```
* DEBUG: デバッグ目的で低いレベルのシステム情報
* INFO: 一般的なシステム情報
* WARNING: 発生した小さな問題についての情報
* ERROR: 発生した大きな問題についての情報
* CRITICAL: 発生した致命的な問題についての情報
```

## settingsでの設定
settings.pyにてloggingの設定を行う。
```
LOGGING = {
    'version': 1,
    'disable_existing_loggers': True,
    'formatters': {
        'verbose': {
            'format': '%(levelname)s %(asctime)s %(module)s %(process)d %(thread)d %(message)s'
        },
        'simple': {
            'format': '%(levelname)s %(message)s'
        },
    },
    'filters': {
        'special': {
            '()': 'project.logging.SpecialFilter',
            'foo': 'bar',
        }
    },
    'handlers': {
        'null': {
            'level':'DEBUG',
            'class':'django.utils.log.NullHandler',
        },
        'console':{
            'level':'DEBUG',
            'class':'logging.StreamHandler',
            'formatter': 'simple'
        },
        'mail_admins': {
            'level': 'ERROR',
            'class': 'django.utils.log.AdminEmailHandler',
            'filters': ['special']
        }
    },
    'loggers': {
        'django': {
            'handlers':['null'],
            'propagate': True,
            'level':'INFO',
        },
        'django.request': {
            'handlers': ['mail_admins'],
            'level': 'ERROR',
            'propagate': False,
        },
        'myproject.custom': {
            'handlers': ['console', 'mail_admins'],
            'level': 'INFO',
            'filters': ['special']
        }
    }
}
```

## formatters
- ログの出力形式を定義できる
- handlerにて`'formatter': ‘simple'`とすることで出力形式を指定できる

## filters
- ログに値を追加したり、特定の条件で表示・非表示のフィルタをかけられる
- この例では、
  - loggerで `'filters': ['special’]` と追加することで指定のloggerが以下の関数でフィルタされる
  - ログに{'foo': ‘bar’}が追加される

```
# project/logging.py
import logging

class SpecialFilter(logging.Filter):
     def filter(self, record):
         record.user = record.request.user_profie['fullName']
         return True
```
return Falseとすれば出力されないようにできる

## handlers
- ログレベルと、それに紐づく動作（標準出力やメール送信など）を定義できる
- ログが発生したときに指定したログレベル以上であれば、指定された動作が実行される

この例では以下のようにハンドラが動作する
```
* null NullHandler です。 DEBUG 以上の全てのメッセージを /dev/null に捨てます。
* console StreamHandler です。 DEBUG 以上の全てのメッセージを標準エ ラー出力に出力します。このハンドラは simple 出力フォーマットを使います。
* mail_admins AdminEmailHandler です。 ERROR 以上の全てのメッセージ をサイト管理者にメール送信します。このハンドラは special フィルタを使 います。
```

## loggers
- ロギングシステムのエントリポイントになる。　　
- ログレベル、ハンドラ、フィルタ、propagate(loggerを親に伝搬させるか)を設定する　　
- 指定したログレベル以上であれば、指定したフィルタ、ハンドラが実行される

ここでは以下の操作が定義されている

```
* django は INFO 以上のメッセージを null ハンドラに渡します。
* django.request は全ての ERROR メッセージを mail_admins ハンド ラに渡します。さらに、このロガーはメッセージを伝播 しない ように印をつけ られています。これにより django に書かれたログメッセージを django ロガーは扱わないことになります。
* myproject.custom は INFO 以上の全てのメッセージと special フィ ルタを 2 つのハンドラ console と mail_admins に渡します。全ての INFO レベル以上のメッセージはコンソールに出力され、 ERROR とCRITICAL メッセージはメール経由で出力されることになります。
```

## ロギングを使う
- 最初にログインスタンスを取得
- 名前にはloggersの名前を指定する
```
logging.getLogger('project.interesting.stuff')
```

その後、ログレベルを指定して実行することでロギングが実行される
```
* logger.critical()
* logger.error()
* logger.warning()
* logger.info()
* logger.debug()
```

## 例
```
# logging ライブラリをインポートする
import logging

# ロガーインスタンスを取得
logger = logging.getLogger('django.request')

def my_view(request, arg1, arg):
    ...
    if bad_mojo:
        # エラーメッセージをログ出力
        logger.error('Something went wrong!')
```
