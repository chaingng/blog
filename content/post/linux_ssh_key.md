---
title: "公開鍵認証によるsshアクセスの設定"
date: 2017-01-01T10:00:00+09:00
tags: [ "linux"]
---

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

### サーバにログインし、 `~/.ssh/authorized_keys` に作成した公開鍵の内容を追加

作成した公開鍵の内容をコピーし、
```
$ cat ~/.ssh/hogefuga.pub
ssh-rsa xxxxx hondatakatomo@hondatakashisatoshinoMacBook-Pro.local
```

`~/.ssh/authorized_keys`に追加する
```
$ cat ~/.ssh/authorized_keys
....
....
ssh-rsa xxxxx hondatakatomo@hondatakashisatoshinoMacBook-Pro.local
```

### /etc/ssh/sshd_config にて公開鍵認証をonにする
PubkeyAuthenticationをyesにすればよい
```
$ cat /etc/ssh/sshd_config 
...
PubkeyAuthentication yes
...
```

### これで秘密鍵によるsshアクセスが可能になる
```
ssh -i ~/.ssh/hogefuga user@hostname
```
