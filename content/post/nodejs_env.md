---
title: "node.jsで環境変数を設定・取得"
date: 2017-04-09T10:00:00+09:00
tags: [ "node.js"]
---

node.jsで環境変数を設定・取得するには[process.env](https://nodejs.org/api/process.html#process_process_env)を使う。

### 目次

- [環境変数の一覧を取得](#環境変数の一覧を取得)
- [特定の環境変数を取得](#特定の環境変数を取得)
- [環境変数の設定と変更](#環境変数の設定と変更)


### 環境変数の一覧を取得
process.envですべての環境変数が取得できる

```
$ node
> process.env
{
  TERM: 'xterm-256color',
  SHELL: '/usr/local/bin/bash',
  USER: 'maciej',
  PATH: '~/.bin/:/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin',
  PWD: '/Users/maciej',
  EDITOR: 'vim',
  SHLVL: '1',
  HOME: '/Users/maciej',
  LOGNAME: 'maciej',
  _: '/usr/local/bin/node'
}
```

<br>

### 特定の環境変数を取得
process.env.XXで特定の環境変数が取得できる

```
> process.env.TERM
'xterm-256color'
```

例えば以下のように使う。
```
var term =  process.env.TERM || 'xterm-512color';
```


<br>

### 環境変数の設定と変更
代入や変更も可能

```
process.env.test = null;
console.log(process.env.test);
// => 'null'
process.env.test = undefined;
console.log(process.env.test);
// => 'undefined'
```
