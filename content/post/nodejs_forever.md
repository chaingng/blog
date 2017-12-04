---
title: "foreverでnode.jsアプリケーションをデーモン化"
date: 2017-12-02T10:00:00+09:00
tags: [ "nodejs"]
---

[forever](https://github.com/foreverjs/forever)を使うことで、nodeまたは任意のスクリプトをデーモン化することができる。


### インストール
```
npm install forever -g
```

<br>

### nodeスクリプトをデーモン起動
```
$ forever start server.js
warn:    --minUptime not set. Defaulting to: 1000ms
warn:    --spinSleepTime not set. Your script will exit if it does not stay up for at least 1000ms
info:    Forever processing file: server.js
```

<br>

### 環境変数を指定して起動
foreverの先頭に環境変数を指定して起動する
```
$ PROGRAM_PORT=8444 forever start server.js
warn:    --minUptime not set. Defaulting to: 1000ms
warn:    --spinSleepTime not set. Your script will exit if it does not stay up for at least 1000ms
info:    Forever processing file: server.js
```

<br>

### foreverで起動しているプログラムの一覧を確認

```
$forever list
info:    Forever processes running
data:        uid  command                                              script    forever pid   id logfile                                uptime
data:    [0] 2qrw /Users/hondatakatomo/.ndenv/versions/v6.9.1/bin/node server.js 30195   30203    /Users/hondatakatomo/.forever/2qrw.log 0:0:0:19.783
```

<br>

### foreverで起動したプログラムの停止
forever stopで`[Id|Uid|Pid|Index|Script]`のいずれかを指定する
```
$ forever stop 30203
info:    Forever stopped process:
    uid  command                                              script    forever pid   id logfile                                uptime
[0] 2qrw /Users/hondatakatomo/.ndenv/versions/v6.9.1/bin/node server.js 30195   30203    /Users/hondatakatomo/.forever/2qrw.log 0:0:1:57.597
```

きちんと停止しているのがわかる
```
$ forever list
info:    No forever processes running
```

<br>

###  すべてのプログラムの停止
```
$forever stopall
```

<br>

### プログラムを再起動
```
$ forever restart server.js
info:    Forever restarted process(es):
data:        uid  command                                              script    forever pid  id logfile                                uptime
data:    [0] lWr2 /Users/hondatakatomo/.ndenv/versions/v6.9.1/bin/node server.js 30517   9439    /Users/hondatakatomo/.forever/lWr2.log 0:0:0:16.294
data:    [1] UIEE /Users/hondatakatomo/.ndenv/versions/v6.9.1/bin/node server.js 9401    9438    /Users/hondatakatomo/.forever/UIEE.log 0:0:0:16.361
```

<br>

### logfileの設定を確認
```
$ forever logs
info:    Logs for running Forever processes
data:        script    logfile
data:    [0] server.js /Users/hondatakatomo/.forever/lWr2.log
```

```
$ cat /Users/hondatakatomo/.forever/lWr2.log
info    - EasyRTC: Starting EasyRTC Server (v1.1.0) on Node (v6.9.1)
debug   - EasyRTC: Emitting event 'startup'
debug   - EasyRTC: Running func 'onStartup'
listening on https://localhost:8444
```

<br>

### optionでログファイルの指定も可能
```
    -l  LOGFILE      Logs the forever output to LOGFILE
    -o  OUTFILE      Logs stdout from child script to OUTFILE
    -e  ERRFILE      Logs stderr from child script to ERRFILE
```

<br>

### (おまけ)Nodeプログラムだけでなく、シェルもデーモン化できる
```
forever -c sh start my_daemon_script.sh
```
