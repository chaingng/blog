---
title: "pipenvの使い方"
date: 2017-12-07T10:00:00+09:00
tags: [ "python"]
---

pipenvを使うことにより、rubyにおけるGemfileのようにpythonでpackage管理を行うことができる。

## いいところ
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
pipenv —three 

# python2系
pipenv --two  
```

## requirements.txtのインポート
```
pipenv install --requirements requirements.txt
```

## packageのインストール
```
pipenv install [package]
```


## Pipfile.lockを使用してインストール
```
pipenv install --ignore-pipfile [package]
```

## [dev-packages]にパッケージをインストール
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

## Pipfile.lockを作成
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

## —systemでhashのチェック
```
$ pipenv install --system
Installing dependencies from Pipfile.lock (f15c0a)…
An error occurred while installing python-socketio==1.8.3! Will try again.
An error occurred while installing python-engineio==1.7.0! Will try again.
An error occurred while installing flask-socketio==2.9.2! Will try again.
  🐍   ▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉ 71/71 — 00:00:53
Installing initially–failed dependencies…
Collecting python-socketio==1.8.3 ▉▉▉ 0/3 — 00:00:00
  Using cached python_socketio-1.8.3-py2.py3-none-any.whl

THESE PACKAGES DO NOT MATCH THE HASHES FROM Pipfile.lock!. If you have updated the package versions, please update the hashes. Otherwise, examine the package contents carefully; someone may have tampered with them.
    python-socketio==1.8.3 from https://pypi.python.org/packages/54/80/ee4dab6e14c749f8591b6aabc7e503147bac35791c6638626f0fd39cda3f/python_socketio-1.8.3-py2.py3-none-any.whl#md5=ce047feda6041303a2415cc34587ffc1 (from -r /var/folders/6p/wpmhc9b92zv5k8j19djbfqj00000gn/T/pipenv-bjoMqA-requirement.txt (line 1)):
        Expected sha256 822433bcda86924367bccfc64083bae60bd64c89c8fc07f79530458ce5a6dcea
             Got        0d4991d2a7424c59ecad492d4c331de26d227aec4d2f49374807ed5c32a46156


  ☤  ▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉ 0/3 — 00:00:00
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
