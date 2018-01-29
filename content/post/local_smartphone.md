---
title: "android/iphoneでローカルサーバに接続する"
date: 2018-01-26T10:00:00+09:00
tags: [ "dev"]
---

### 1.ローカルサーバを立ち上げているPCとスマートフォンを同じwifiに接続

### 2. Internet共有を有効にする
macであれば`システム環境設定＞共有`から図のとおり設定

<img width="650" alt="2018-01-29 10 52 53" src="https://user-images.githubusercontent.com/3523368/35490409-d2a36fda-04e2-11e8-854b-1b6ddfad86e5.png">


### 3. PCのIPアドレスを確認
macであれば`システム環境設定＞ネットワーク`から確認できる

<img width="663" alt="2018-01-25 14 33 16" src="https://user-images.githubusercontent.com/3523368/35439234-398d66ea-02dd-11e8-9fbc-c383cf44f335.png">

### 4.確認したIPアドレスを指定して接続可能
上記の例であれば、 `http://192.168.10.199:8080`で接続できる（ポート名は立ち上げているサーバに合わせて変える）
