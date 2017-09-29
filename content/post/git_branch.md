---
title: "リモート追跡ブランチ／追跡ブランチ／リモートブランチの違い"
date: 2017-07-16T00:00:00+09:00
---

# まとめ

## リモートブランチ
```
- リモートレポジトリに存在するブランチ
- (remote)/(branch)で表される
```

## リモート追跡ブランチ
```
- ローカルに存在
- リモートブランチの状態を保持するブランチ
- リモートへpushすると自動的に作成される
- fetchでローカルのリモート追跡ブランチの状態が最新化される
```

## 追跡ブランチ

```
- リモートブランチと直接のつながりをもつローカルブランチ
- git branch / git checkoutにて作成可能
- git push時にブランチ名が省略可能
```

# リモート追跡ブランチ

## リモート追跡ブランチの定義

[3.5 Git のブランチ機能 - リモートブランチ](https://git-scm.com/book/ja/v2/Git-%E3%81%AE%E3%83%96%E3%83%A9%E3%83%B3%E3%83%81%E6%A9%9F%E8%83%BD-%E3%83%AA%E3%83%A2%E3%83%BC%E3%83%88%E3%83%96%E3%83%A9%E3%83%B3%E3%83%81)より、リモートブランチの状態を持つ参照状態であることがわかる

```
リモート追跡ブランチは、リモートブランチの状態を保持する参照です。 
ローカルに作成される参照ですが、自分で移動することはできません。ネットワーク越しの操作をしたときに自動的に移動します。 
リモート追跡ブランチは、前回リモートリポジトリに接続したときにブランチがどの場所を指していたかを示すブックマークのようなものです。
```

## リモート追跡ブランチの表示

`git branch -a`でリモート追跡ブランチを含むブランチを表示する。

```
$ git branch -a
* develop
  remotes/origin/demo
  remotes/origin/demo2
  remotes/origin/demo3
  remotes/origin/HEAD -> origin/develop
```

このときreotes/(remote)/(branch)で表されるのがリモート追跡ブランチ。  
最後の行はリモートブランチorigin/developがリモート追跡ブランチremotes/origin/HEADに紐付いていることを表す。

## リモート追跡ブランチの更新

[git-fetch](https://git-scm.com/docs/git-fetch)より、`git fetch`でリモート追跡ブランチが最新化されると書いてある。
```
Fetch branches and/or tags (collectively, "refs") from one or more other repositories, 
along with the objects necessary to complete their histories. 
Remote-tracking branches are updated (see the description of <refspec> below for ways to control this behavior).
```

```
$ git branch -a
* demo2
  demo3
  develop
  remotes/origin/DEV-475
  remotes/origin/demo
  remotes/origin/demo2
  remotes/origin/demo3

$ git fetch
$ git branch -a
* demo2
  demo3
  develop
  remotes/origin/DEV-475
  remotes/origin/demo
  remotes/origin/demo2
  remotes/origin/demo3
  remotes/origin/dev
```

前回fetchしてから誰かがorigin/devを作成し、  
新しくremotes/origin/devがリモート追跡ブランチとして追加されていることがわかる。


# 追跡ブランチ

## 追跡ブランチの定義

[3.5 Git のブランチ機能 - リモートブランチ](https://git-scm.com/book/ja/v2/Git-%E3%81%AE%E3%83%96%E3%83%A9%E3%83%B3%E3%83%81%E6%A9%9F%E8%83%BD-%E3%83%AA%E3%83%A2%E3%83%BC%E3%83%88%E3%83%96%E3%83%A9%E3%83%B3%E3%83%81)より、リモートブランチと直接のつながりをもつブランチであることがわかる。

```
リモート追跡ブランチからローカルブランチにチェックアウトすると、
“追跡ブランチ” というブランチが自動的に作成されます(そしてそれが追跡するブランチを`‘上流ブランチ’'といいます)。
追跡ブランチとは、リモートブランチと直接のつながりを持つローカルブランチのことです。 
追跡ブランチ上で git pull を実行すると、Git は自動的に取得元のサーバーとブランチを判断します。
```

## 追跡ブランチの作成

`git branch (branch) (remote tracking branch)`で追跡ブランチを作成  
リモート追跡ブランチを選択する。　

```
$ git branch demo3 origin/demo3
Branch demo3 set up to track remote branch demo3 from origin.
```

checkoutも同時に行いたいとき

```
$ git checkout -b demo2 origin/demo2
Branch demo2 set up to track remote branch demo2 from origin.
Switched to a new branch 'demo2'
```

以下でも同じ
```
$ git checkout --track origin/demo2
Branch demo2 set up to track remote branch demo2 from origin.
Switched to a new branch 'demo2'
```

## ローカルブランチを追跡ブランチにする

git branch -u で可能

```
$ git branch -u origin/serverfix
Branch serverfix set up to track remote branch serverfix from origin.
```

## ローカルブランチが追跡ブランチか確認

git branch -vvを使う

```
$ git branch -vv
  iss53 7e424c3 [origin/iss53: ahead 2] forgot the brackets
  master 1ae2a45 [origin/master] deploying index fix
* serverfix f8674d9 [teamone/server-fix-good: ahead 3, behind 1] this should do it
  testing 5ea463a trying something new
```

このときiss53はorigin/iss53、master、serverfixは追跡ブランチで、testingは追跡ブランチではないことがわかる。


## 追跡ブランチではgit pushでブランチ名が省略できる

追跡ブランチは、`git push`にてブランチ名が省略可能。  
省略時は追跡しているリモートブランチにpushする。

```
$ git push origin
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 306 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To github.com:xxx/xxx.git
  0d66e69..ee7b38f  demo2 -> demo2
```
