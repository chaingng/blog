---
title: "linuxとmacにおける検索"
date: 2018-01-07T10:00:00+09:00
tags: [ "linux"]
---

# コマンドに対する検索

## which
指定されたコマンドの場所を調べる 

```
$ which python
/Users/hondatakatomo/.pyenv/shims/python
```

オプション-aですべて調べる
```
$ which -a python
/Users/hondatakatomo/.pyenv/shims/python
/usr/bin/python
```

## whereis
指定されたコマンドのバイナリーファイル,ソースコード,マニュアルファイルの場所を検索

- -b バイナリファイルだけ探す
- -m マニュアルだけ探す
- -B ディレクトリを指定して探す

# ファイルシステムの検索

## locate

あらかじめデータベースを作成しておくことで、高速に検索する

```
$ locate OUTPUT.mobi
/Users/hondatakatomo/github/flask_book/OUTPUT.mobi
```

### linuxでのデータベースの作成

```
updatedb
```

### macでのデータベースの作成

作成しないと以下のエラーがでる

```
$ locate sample
> WARNING: The locate database (/var/db/locate.database) does not exist.
To create the database, run the following command:

  sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.locate.plist

Please be aware that the database can take some time to generate; once
the database has been created, this message will no longer appear.
```

これに従ってデータベースを作成
```
sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.locate.plist
```


## find
都度ファイルシステムすべてを探して検索

- -type f　ファイルに対して検索
- -type d ディレクトリに対して検索

```
$ find / -name OUTPUT.mobi
/Users/hondatakatomo/Library/Application Support/Kindle/My Kindle Content/OUTPUT.mobi
/Users/hondatakatomo/github/flask_book/OUTPUT.mobi
```

## mdfind
macではSpotlightコマンドである、mdfindコマンドが存在する。  
これは、mac Spotlightのデーモンによって常にデータベースは更新されているのでデータベースの手動更新が不要で、拘束に検索できる

```
$ mdfind OUTPUT.mobi
/Users/hondatakatomo/Library/Application Support/Kindle/My Kindle Content/OUTPUT.mobi
/Users/hondatakatomo/github/flask_book/OUTPUT.mobi
```
