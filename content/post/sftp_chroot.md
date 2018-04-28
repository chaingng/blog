---
title: "sftpでユーザがアクセスできるディレクトリを制限する"
date: 2018-04-26T10:00:00+09:00
tags: [ "library"]
---

sftpでユーザがアクセスできるディレクトリを制限するには、chroot設定を行う。

同時にsftpのみ許可し、sshアクセスできないようにも制限できる。

## 目次
- [ユーザホームフォルダをroot所有に変更](#ユーザホームフォルダをroot所有に変更)
- [sshd_configを修正し、chrootを有効化する](#sshd_configを修正し、chrootを有効化する)
- [sshdサービスを再起動して設定を有効化](#sshdサービスを再起動して設定を有効化)
- [アップロード用のディレクトリを作成](#アップロード用のディレクトリを作成)
- [動作確認](#動作確認)

## ユーザホームフォルダをroot所有に変更
chrootではホームフォルダをroot所有に変更する必要があるため、以下のように変更する。

```
chown root:root /home/[user]
```

`/home/[user]`はユーザのホームディレクトリ。


## sshd_configを修正し、chrootを有効化する
`/etc/ssh/sshd_config`にて、以下の設定を追加する。

```
Match User [user]
  ChrootDirectory /home/%u
  ForceCommand internal-sftp
```

`%u`はユーザ名で、`/home/[user]`ディレクトリが指定されることになる。
また、`internal-sftp`コマンドを指定することで、sshアクセスもできないように制限できる。

## sshdサービスを再起動して設定を有効化

```
service sshd restart
```

## アップロード用のディレクトリを作成
ホームフォルダはroot所有にしているため、ファイルのダウンロードはできてもファイルのアップロードはできない。  

また、write権限を与えるとchrootによるログインができなくなるので、ホームフォルダのパーミッションを変更することもできない。

そのため、ホームフォルダ以下にアップロード用のディレクトリを作成する。
　
```
mkdir /home/[user]/upload
```

作成したアップロード用のディレクトリを、ユーザ所有に変更する。

```
chmod [user]:[user] /home/[user]/upload
```

これで、uploadフォルダ以下はユーザがファイルアップロード可能になる。


## 動作確認

sshアクセスできるか試してみる。
```
$ ssh -i ~/.ssh/[secret_key] hoge@xxx.xxx.xxx.xxx
This service allows sftp connections only.
Connection to xxx.xxx.xxx.xxx closed.
```

sftpのみしかコネクション許可していない、というメッセージがでてsshアクセスはできなくなっている。

sftpアクセスしてみる。
```
sftp -i ~/.ssh/[secret_key] hoge@xxx.xxx.xxx.xxx
Connected to xxx.xxx.xxx.xxx.
```

正しく接続できた。
現在のディレクトリを確認してみる。

```
sftp> pwd
Remote working directory: /
```

`/`となっており、ホームフォルダ以外のディレクトリに移動できないようになった。

upload以下にファイルがアップロードできるか試してみる。

```
> put example.log upload/
Uploading example.log to /upload/example.log
example.log                          100%   81     6.6KB/s   00:00
```

正しくアップロードできることも確認できた。
