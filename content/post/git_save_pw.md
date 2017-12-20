---
title: "gitでパスワードを保存する"
date: 2017-04-02T10:00:00+09:00
tags: [ "git"]
---

httpsアクセスの際、githubへのアクセスにはパスワード or personal access token（二段階認証を設定している場合）が必要になる。  
デフォルトでは、アクセスの際に毎回入力が求められる。  
[credential.helper](https://git-scm.com/book/ja/v2/Git-%E3%81%AE%E3%81%95%E3%81%BE%E3%81%96%E3%81%BE%E3%81%AA%E3%83%84%E3%83%BC%E3%83%AB-%E8%AA%8D%E8%A8%BC%E6%83%85%E5%A0%B1%E3%81%AE%E4%BF%9D%E5%AD%98) コマンドでローカルに認証情報を保存することで、以降の入力が不要になる。

### credential.helperの保存モード

- casheモード
  - 認証情報が一定時間メモリに保存される
  - デフォルトは15分だが、変更可能
- storeモード
  - 認証情報をテキストファイルに保存する
  - 永続的な保存が可能だが、平文でパスワードが保存される
- osxkeychainモード
  - Macを使っている場合にOS のキーチェーンに認証情報がキャッシュされる
  - 暗号化され、永続的に保存される
- wincredモード
  - windowsを使っているときに, Mac OSと似た仕組みで保存可能
  
<br>

### cashモード

```
git config --global credential.helper cache
```

タイムアウト時間を変更したい場合
```
# タイムアウト時間を3600秒に設定
git config --global credential.helper 'cache --timeout=3600'
```

<bf>

### storeモード
```
git config --global credential.helper store
```

デフォルトでは~/.git-credentialsに保存される。保存先を変更したいとき
```
git config --global credential.helper store --file ~/.hoge-credentials
```

デフォルトでは永続的に保存される。有効期限の設定も可能
```
[credential]
    helper = store --file /mnt/thumbdrive/.git-credentials
    helper = cache --timeout 30000
```

<br>

### osxkeychainモード
```
git config --global credential.helper osxkeychain
```
