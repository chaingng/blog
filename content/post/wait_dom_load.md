---
title: "assetsの読み込み前にDOMの制御をしたい場合はDOMContentLoadedを使う"
date: 2018-01-29T10:00:00+09:00
tags: [ "javascript"]
---

すべてのCSSや画像などのassetsの読み込みまで待つのは時間がかかってしまうので避けたい。

しかしDOMの制御をするためにDOMの読み込みをすべて待ってから処理をしたい場合は、[DOMContentLoaded](https://developer.mozilla.org/ja/docs/Web/Reference/Events/DOMContentLoaded)を使う。

## DOMContentLoaded

DOMContentLoaded イベントは、最初のHTMLドキュメントの読み込みと解析が完了した時に発火する。  
スタイルシートや画像、サブフレームの読み込みが終わるのを待たない。

```
<script type="text/javascript">
  document.addEventListener('DOMContentLoaded', function() {
    var div = document.getElementById("domain-name");
    div.textContent = 'hogefuga';
  });
</script>
```

## load
ページが完全に読み込み終わったときに処理をしたい場合は、[load](https://developer.mozilla.org/en-US/docs/Web/Events/load)を使用する

```
<script>
  window.addEventListener("load", function(event) {
    console.log("All resources finished loading!");
  });
</script>
```
