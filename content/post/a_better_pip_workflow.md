---
title: "[要約]A Better Pip Workflow"
date: 2017-03-12T00:00:00+09:00
tags: [ "python"]
---

requirements.txtを使うのには問題があるよ、という話。



### 典型的なrequirements.txtの使い方

#### １．A list of top-level dependencies a project has, often without versions specified.  
PJのトップレベル依存リストとして、バージョン指定なしで使う

```
$ cat requirements.txt
requests[security]
flask
gunicorn==19.4.5
```

- シンプルな使い方
- productionで使おうとすると、予期せぬ結果が起こりうる
- 理由はバージョン指定をしていないからで、日々起こる結果がかわってしまう

#### ２．A complete list of all dependencies a project has, each with exact versions specified.  
プロジェクトの完全なのdependencies listとしてバージョン指定をして使う

```
$ cat requirements.txt
cffi==1.5.2
cryptography==1.2.2
enum34==1.1.2
Flask==0.10.1
gunicorn==19.4.5
idna==2.0
ipaddress==1.0.16
itsdangerous==0.24
Jinja2==2.8
MarkupSafe==0.23
ndg-httpsclient==0.4.0
pyasn1==0.1.9
pycparser==2.14
pyOpenSSL==0.15.1
requests==2.9.1
six==1.10.0
Werkzeug==0.11.4
```

- アプリケーションのデプロイとしてはベストプラクティス
- すべてのdependenciesはsub-dependenciesも含めてリストされる
- このタイプは現在のアプリケーション実行環境からpip freezeによって生成されたリスト
- でもちょっとcumbersome（やっかい）
- すべてのパッケージについてまとめて`pip install --upgrade`をやろうとしたときに簡単ではない
- １つ１つリストをみながら`$ pip install requests[security] flask --upgrade`とやっていく必要がある

## ベターなWorkFlow

#### ２つファイルを用意する

```
requirements-to-freeze.txt
requirements.txt
```

requirements-to-freeze.txtはこんな感じ
```
$cat requirements-to-freeze.txt
requests[security]
flask
gunicorn==19.4.5
```

requirements.txtはこんな感じ
```
$cat requirements.txt
cffi==1.5.2
cryptography==1.2.2
enum34==1.1.2
Flask==0.10.1
gunicorn==19.4.5
idna==2.0
ipaddress==1.0.16
itsdangerous==0.24
Jinja2==2.8
MarkupSafe==0.23
ndg-httpsclient==0.4.0
pyasn1==0.1.9
pycparser==2.14
pyOpenSSL==0.15.1
requests==2.9.1
six==1.10.0
Werkzeug==0.11.4
```

#### Workflow
requirements-to-freeze.txtはメソッド１として使い、
requirements.txtはメソッド２で使う

#### 使用例
```
$ cd project-repo

$ pip install -r requirements-to-freeze.txt --upgrade
Installing collected packages: six, enum34, ipaddress, ...

$ pip freeze > requirements.txt
```

### 所感

このように２つworkflowもあるけれど、著者のPipenvを使う裏付けとして理解しておきたい

