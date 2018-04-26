---
title: "公開鍵によるsshアクセスの設定"
date: 2017-01-01T10:00:00+09:00
tags: [ "linux"]
---

### 手順
- [ssh-keygenにて公開鍵と秘密鍵を作成](#ssh-keygenにて公開鍵と秘密鍵を作成)
- [秘密鍵のパーミッションを変更](#秘密鍵のパーミッションを変更)
- [サーバにて対象ユーザのauthorized_keysに作成した公開鍵の内容を追加](#サーバにて対象ユーザのauthorized_keysに作成した公開鍵の内容を追加)
- [sshd_condigにて公開鍵認証をON](#sshd_condigにて公開鍵認証を有効化)
- [sshdサービスを再起動し設定を有効化](#sshdサービスを再起動し設定を反映)
- [秘密鍵によるsshアクセスできるか確認](#秘密鍵によるsshアクセスできるか確認)

### ssh-keygenにて公開鍵と秘密鍵を作成

```
$ ssh-keygen -t rsa -b 2048
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/hondatakatomo/.ssh/id_rsa): /Users/hondatakatomo/.ssh/hogefuga
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /Users/hondatakatomo/.ssh/hogefuga.
Your public key has been saved in /Users/hondatakatomo/.ssh/hogefuga.pub.
The key fingerprint is:
SHA256:6ax5ZpcLwzdG0n+XyK9j4jPMiRHjtmXU2cnXtQGoenM hondatakatomo@hondatakashisatoshinoMacBook-Pro.local
The key's randomart image is:
+---[RSA 2048]----+
|            ...  |
|           .   ..|
|          . . + *|
|         * . o =o|
|        S *     .|
|       = O E. . .|
|        O #.oo...|
|       o+BoO +.. |
|      o+ .oo=.o. |
+----[SHA256]-----+
```

### 秘密鍵のパーミッションを変更
```
chmod 400 /Users/hondatakatomo/.ssh/hogefuga
```

### サーバにて対象ユーザのauthorized_keysに作成した公開鍵の内容を追加

作成した公開鍵の内容をコピーし、
```
$ cat ~/.ssh/hogefuga.pub
ssh-rsa xxxxx hondatakatomo@hondatakashisatoshinoMacBook-Pro.local
```

対象ユーザの`/home/[user]/.ssh/authorized_keys`に追加(`[user]`はユーザ名)

```
$ vi ~/.ssh/authorized_keys
....
....
ssh-rsa xxxxx hondatakatomo@hondatakashisatoshinoMacBook-Pro.local
```


### sshd_condigにて公開鍵認証を有効化

`/etc/ssh/sshd_config`にて、PubkeyAuthenticationをyesにする

```
$ cat /etc/ssh/sshd_config 
...
PubkeyAuthentication yes
...
```

### sshdサービスを再起動し設定を反映
```
service sshd restart
```

### 秘密鍵によるsshアクセスできるか確認

これで秘密鍵によるsshアクセスが可能になる
```
ssh -i ~/.ssh/hogefuga user@hostname
```
