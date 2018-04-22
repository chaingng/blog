---
title: "Stackの基礎"
date: 2017-12-17T10:00:00+09:00
tags: [ "algorithm"]
---

## 概要
- pushとpopが基本動作。LIFO
- time O(1)
- 配列で実装可能
- peek操作もある（要素の山椒の実で取り出さない）

## 8.1 MAX値を返せるStackの実装

### brute-force
- クエリのたびにmaxを調べる
- time O(n), space O(1)

### improved solution
- ノードにその時点のmax値を持たせる
- time O(1), space O(n)

### solution
- max値を更新したときのみ配列に持たせる　
- time O(1), space from O(1) to O(n)

