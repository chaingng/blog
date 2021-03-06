---
title: "[linux]シグナルとkill"
date: 2018-01-05T10:00:00+09:00
tags: [ "linux"]
---

## シグナルとは

シグナルとは、プロセスに対して通知するイベント。

シグナルを受け取ったプロセスは現在実行中の処理を中断し、シグナルに応じた処理を実行する。

具体的には、killやCtrl+hogeでシグナルを発生させることができる。

## 代表的なシグナル

| シグナル | killコマンド | Ctrlコマンド |意味|
|:-----------|------------:|:------------:|:------------:|
SIGHUP|kill -1|-|ハングアップ（端末の切断などで発生）|
SIGINT|kill -2|Ctrl+C|割り込みの発生|
SIGKILL|kill -9|-|プロセスの強制終了|
SIGTERM|kill -15|-|プロセスの終了|
SIGTSTP|kill -TSTP|Ctrl+Z|プロセスの一時停止|

シグナルを受け取ったプロセスは、シグナルごとに定義された処理が実行される。
ただし、SIGKILLはプロセスの外部からプロセスを終了させるのでプロセスで独自の処理を定義できない。


## Ctrl+hogeの正体

Ctrl＋hogeが入力されると、以下で定義されたシグナルが送信される。
シグナルの送信先は、フォアグラウンドで動いているプロセスグループに属するすべてのプロセス。
```
stty -a
```

ちなみに、Ctrl + DはEOFをプロセスに送っている。

## kill
シグナルの送信先は、指定されたプロセスのみ（プロセスグループではない）。
