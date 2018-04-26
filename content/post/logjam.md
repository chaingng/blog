---
title: "logjam脆弱性と対策"
description : "Weak Diffie-Hellman and the Logjam Attackが公式ソース。こちらに書かれている、脆弱性と対策は以下の通り。"
date: 2017-03-26T10:00:00+09:00
tags: [ "security"]
---

logjamとは、DH鍵交換に存在する脆弱性を利用した攻撃。  
公式ソースである[Weak Diffie-Hellman and the Logjam Attack](https://weakdh.org/)に書かれている、脆弱性の詳細と対策についてまとめる。


## 目次
- [logjamとは](#logjamとは)
- [サーバに脆弱性があるかのテスト](#サーバに脆弱性があるかのテスト)
- [クライアントブラウザの脆弱性テスト](#クライアントブラウザの脆弱性テスト)
- [対策](#対策)
- [TLSにおけるDiffie-Hellman設定のためのガイド](#TLSにおけるDiffie-Hellman設定のためのガイド)

## logjamとは

ディフィー・ヘルマン鍵交換における脆弱性を利用した攻撃

- TLSプロトコルに対する攻撃
    - 中間者攻撃によりTLSコネクションを512ビットの暗号強度まで弱くすることができる
    - 暗号化スイートとしてDHE_EXPORTをサポートする、あらゆるサーバに影響がある

- ステートレベルでの脅威
    - HTTPS, SSH, and VPNサーバはDH鍵交換に同じ素数を使っており、脆弱性ははこの素数に依存する

<br>

## サーバに脆弱性があるかのテスト

[TLS Logjam Check](https://tools.keycdn.com/logjam)にてテストする。

<img width="1101" alt="2017-10-01 12 22 39" src="https://user-images.githubusercontent.com/3523368/31051448-8a0cc098-a6a3-11e7-950a-7d075160d7dc.png">

**Warning**と出れば要対策。

<br>

## クライアントブラウザの脆弱性テスト

[SSL/TLS Capabilities of Your Browser](https://www.ssllabs.com/ssltest/viewMyClient.html)にてテストする。


<img width="1215" alt="2017-10-01 12 23 41" src="https://user-images.githubusercontent.com/3523368/31051447-88749c9c-a6a3-11e7-9075-1c3418040d26.png">

Logjam Vulnerabilityにて**Your user agent is not vulnerable**と出れば問題ない。

<br>

## 対策

<br>

### クライアント

Google Chrome (including Android Browser), Mozilla Firefox, Microsoft Internet Explorer, and Apple Safariの
最新版はすでにlogjam対策がなされている。  

よって、ブラウザの最新版を利用すれば問題ない。

<br>

### システム管理者or 開発者

- TLSライブラリを最新化する
- サーバでは2048ビット以上の暗号強度にする
- クライアントでは1024ビット以下のDH鍵を使った場合に拒否するようにする

<br>

### サーバー

- webサーバ、メールサーバ
  - 輸出グレードの暗号スイートを禁止する
  - 2048ビットのDiffie-Hellman groupを使用する
- SSH
  - サーバ、クライアントともに最新のOpenSSHを使用するようにする
  - OpenSSHではElliptic-Curve Diffie-Hellman Key Exchangeを推奨する

詳細については、[ Guide to Deploying Diffie-Hellman for TLS](https://weakdh.org/sysadmin.html)　に従って対策を行う

<br>

## TLSにおけるDiffie-Hellman設定のためのガイド

対策方法まとめ

- 輸出グレードの暗号スイートを無効化
  - すでに主要なブラウザは輸出暗号を利用しないようになっている
- Elliptic-Curve Diffie-Hellman (ECDHE)を利用
- より強固なDiffie Hellmanグループを利用
  - 2048ビット以上の暗号キーを使用
  - 安全な素数を使用

<br>

### 強固なDiffie Hellmanグループを利用するための設定

opensslの場合
```
openssl dhparam -out dhparams.pem 2048
```

<br>

### nginxでの設定

`/etc/nginx/sites-enabled/default`にて以下のように更新

暗号スイートを設定
```
ssl_ciphers 'ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:DHE-DSS-AES128-GCM-SHA256:kEDH+AESGCM:ECDHE-RSA-AES128-SHA256:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA:ECDHE-ECDSA-AES256-SHA:DHE-RSA-AES128-SHA256:DHE-RSA-AES128-SHA:DHE-DSS-AES128-SHA256:DHE-RSA-AES256-SHA256:DHE-DSS-AES256-SHA:DHE-RSA-AES256-SHA:AES128-GCM-SHA256:AES256-GCM-SHA384:AES128-SHA256:AES256-SHA256:AES128-SHA:AES256-SHA:AES:CAMELLIA:DES-CBC3-SHA:!aNULL:!eNULL:!EXPORT:!DES:!RC4:!MD5:!PSK:!aECDH:!EDH-DSS-DES-CBC3-SHA:!EDH-RSA-DES-CBC3-SHA:!KRB5-DES-CBC3-SHA';

ssl_prefer_server_ciphers on;
```

DHパラメータを設定
```
ssl_dhparam {path to dhparams.pem};
```

最後に、設定をリロード
```
sudo nginx -s reload
```
### OpenSSHでの設定

OpenSSHはlogjam攻撃に対しては安全であるが
多くのSSH実装では固定の素数を使っていたり、1024ビットの暗号キーが含まれていたりする

もっとも簡単な対策としては、クライアントにelliptic-curve Diffie-Hellman（特に Curve 25519）を使うよう
強制すること

```
KexAlgorithms curve25519-sha256@libssh.org
```

レアなケースかもしれないが、もしelliptic-curveでないDiffie-Hellmanを使いたい場合

- Group 1 を無効にする
- diffie-hellman-group1-sha1鍵交換も無効にする

```
ssh-keygen -G moduli-2048.candidates -b 2048
ssh-keygen -T moduli-2048 -f moduli-2048.candidates
```
