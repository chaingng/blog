---
title: "pipenvの使い方"
date: 2017-04-23T10:00:00+09:00
tags: [ "python"]
---

pipenvを使うことにより、rubyにおけるGemfileのようにpythonでpackage管理を行うことができる。

## 目次
- [利点](#利点)
- [特徴](#特徴)
- [インストール](#インストール)
- [初期化](#初期化)
- [requirements.txtのインポート](#requirementsのインポート)
- [packageのインストール](#packageのインストール)
- [Pipfile.lockを使用してインストール](#Pipfilelockを使用してインストール)
- [dev-packagesにパッケージをインストール](#dev-packagesにパッケージをインストール)
- [packageのアンインストール](#packageのアンインストール)
- [全てのpackageのアンインストール](#全てのpackageのアンインストール)
- [packageのアップデート](#packageのアップデート)
- [Pipfile.lockを作成](#Pipfilelockを作成)
- [packageの依存グラフを確認](#packageの依存グラフを確認)
- [仮想環境でコマンドを実行](#仮想環境でコマンドを実行)
- [仮想環境が有効化されたシェルを起動](#仮想環境が有効化されたシェルを起動)
- [セキュリティの脆弱性をチェック](#セキュリティの脆弱性をチェック)
- [仮想環境の情報を出力](#仮想環境の情報を出力)
- [python_versionを指定](#python_versionを指定)
- [pipenvとpipをアップデート](#pipenvとpipをアップデート)
- [.envのlocationを指定](.envのlocationを指定)
- [.envを読み込まない](.envを読み込まない)
- [jumbotron](#jumbotron)

## 利点
* pip と virtualenv が連係して動作
* requirements.txt ファイルの管理は 問題になり得る ので、代わりにPipenvは来たるべき Pipfile および Pipfile.lock を使う 
* パッケージの依存性をグラフで洞察できる(pipenv graph)
* .envファイルを利用して開発ワークフローを効率化できる

## 特徴
* pyenvが使える場合は、指定されているpythonバージョンを自動でインストールする
* Pipfileが存在しない場合、自動で生成する
* .envファイルがある場合、自動で読み込む
* 既存の仮想環境が存在しないときは、自動で作成
    * 明示的に作る必要がない
* install にパラメータが何も渡されないときは、 [packages] に指定された全てのパッケージがインストール
    * Rubyにおけるbundleと同じ
    

## インストール
```
pip install pipenv
```

## 初期化
python2系 or ３系を指定する。Pipfileが作成される
```
# python3系
pipenv —-three 

# python2系
pipenv --two  
```

## requirementsのインポート
```
pipenv install --requirements requirements.txt
```

## packageのインストール
```
pipenv install [package]
```


## Pipfilelockを使用してインストール
```
pipenv install --ignore-pipfile [package]
```

## dev-packagesにパッケージをインストール
```
pipenv install [package] --dev
```

## packageのアンインストール
```
pipenv uninstall [package]
```

## 全てのpackageのアンインストール
```
$ pipenv uninstall --all
No package provided, un-installing all dependencies.
Found 25 installed package(s), purging...
...
Environment now purged and fresh!
```

## packageのアップデート
package指定がなければ、で全てのパッケージをアップデート
```
pipenv update [package]
```

## Pipfilelockを作成
```
$ pipenv lock
Locking [dev-packages] dependencies…
Locking [packages] dependencies…
Updated Pipfile.lock (58dd91)!
```

## packageの依存グラフを確認
```
$ pipenv graph
awscli==1.14.3
  - botocore [required: ==1.8.7, installed: 1.8.7]
    - docutils [required: >=0.10, installed: 0.14]
    - jmespath [required: <1.0.0,>=0.7.1, installed: 0.9.3]
    - python-dateutil [required: <3.0.0,>=2.1, installed: 2.6.1]
      - six [required: >=1.5, installed: 1.11.0]
  - colorama [required: >=0.2.5,<=0.3.7, installed: 0.3.7]
  - docutils [required: >=0.10, installed: 0.14]
  - PyYAML [required: <=3.12,>=3.10, installed: 3.12]
  - rsa [required: >=3.1.2,<=3.5.0, installed: 3.4.2]
    - pyasn1 [required: >=0.1.3, installed: 0.4.2]
  - s3transfer [required: <0.2.0,>=0.1.12, installed: 0.1.12]
    - botocore [required: <2.0.0,>=1.3.0, installed: 1.8.7]
      - docutils [required: >=0.10, installed: 0.14]
      - jmespath [required: <1.0.0,>=0.7.1, installed: 0.9.3]
      - python-dateutil [required: <3.0.0,>=2.1, installed: 2.6.1]
        - six [required: >=1.5, installed: 1.11.0]
    - futures [required: <4.0.0,>=2.2.0, installed: 3.2.0]
boto==2.48.0
```

## 仮想環境でコマンドを実行
```
pipenv run [command]
pipenv run python run.py
```

## 仮想環境が有効化されたシェルを起動
```
$ pipenv shell
Spawning environment shell (/bin/bash). Use 'exit' to leave.
source /Users/hondatakatomo/.local/share/virtualenvs/webkadai-_nqIBXqd/bin/activate
```

## セキュリティの脆弱性をチェック
現在の環境がPEP 508の要求仕様を満たしているかチェック
```
$ pipenv check
Checking PEP 508 requirements…
Passed!
Checking installed package safety…
All good!
```

## 仮想環境の情報を出力
```
$ pipenv --venv
/Users/hondatakatomo/.local/share/virtualenvs/webkadai-_nqIBXqd
```

## python_versionを指定
pyenv のインストールと設定が済んでいて、必要とするバージョンのPythonがまだ利用できる状態になっていない場合、Pipenvは自動でそのバージョンのPythonをインストールしたいかどうかを尋ねます
```
$ cat Pipfile
[[source]]
url = "https://pypi.python.org/simple"
verify_ssl = true

[dev-packages]

[packages]
requests = "*"

[requires]
python_version = "3.6"
```

## pipenvとpipをアップデート
```
pipenv --update
```

## .envのlocationを指定
```
$ PIPENV_DOTENV_LOCATION=/path/to/.env pipenv shell
```

## .envを読み込まない
```
$ PIPENV_DONT_LOAD_ENV=1 pipenv shell
```

## jumbotron
```
$ pipenv --jumbotron

 _______   __                                           __
/       \ /  |                                         /  |
$$$$$$$  |$$/   ______    ______   _______   __     __ $$ |
$$ |__$$ |/  | /      \  /      \ /       \ /  \   /  |$$ |
$$    $$/ $$ |/$$$$$$  |/$$$$$$  |$$$$$$$  |$$  \ /$$/ $$ |
$$$$$$$/  $$ |$$ |  $$ |$$    $$ |$$ |  $$ | $$  /$$/  $$/
$$ |      $$ |$$ |__$$ |$$$$$$$$/ $$ |  $$ |  $$ $$/    __
$$ |      $$ |$$    $$/ $$       |$$ |  $$ |   $$$/    /  |
$$/       $$/ $$$$$$$/   $$$$$$$/ $$/   $$/     $/     $$/
              $$ |
              $$ |
              $$/
```
