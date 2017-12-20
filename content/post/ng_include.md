---
title: "ng-includeで読み込んだパーシャルをキャッシュさせない"
date: 2017-03-05T10:00:00+09:00
tags: [ "angularjs"]
---

angularjsにてhtmlをパーシャルしたい場合は、`ng-include`を使う。

```
<div ng-include="'views/home/sidebar/_issue_list.html'"></div>
```

## パーシャルが常にcacheされてしまう

ただしこの場合、パーシャルの内容を更新しても`If-Modified-Since`ヘッダが働かないようで、
アプリケーションに更新内容が反映されないという問題がある。

開発時も毎回ブラウザキャッシュしなければならないのでつらい。

stackoverflowでも議論されているけれど、`$templateCache.remove_all()`しても効かない模様。

## 解決方法

そこで、directive化に加え、バージョン番号のクエリを付与することで  
cacheさせずに常に最新の内容を読み込ませることが可能になる。

directive
```
# issue-list.js

(function() {

  angular
    .module('app')
    .directive('issuelist', issueList);

    function issueList() {
        var directive = {
            restrict: "A",
            templateUrl: `./views/home/sidebar/_issue_list.html?v=${new Date().getTime()}`
        }
        return directive;
    }

})();
```

呼び出し側
```
# home.html
<div issuelist></div>
```

開発時はタイムスタンプでもよいけれど、productionではビルド番号を指定するようにしておけば  
ビルドしたときだけ読み込まれるようになる。
