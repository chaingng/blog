---
title: "High Sierra以降のmacはftpとtelnetが使えない。使うには、inetutilsをインストールする。"
date: 2018-04-06T10:00:00+09:00
tags: [ "mac"]
---

[こちら](https://discussions.apple.com/thread/8093031)の公式Q&Aにあるとおり、
High Sierra以降のmacではセキュリティを担保するために、ftpとtelnetがデフォルトで使えない。

## inetutilsのインストール

[inetutils](https://www.gnu.org/software/inetutils/)をインストールすればftpとtelnetが使えるようになる。

```
brew install inetutils
```
