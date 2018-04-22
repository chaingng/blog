---
title: "ハッシュテーブルの概要"
date: 2018-01-08T10:00:00+09:00
tags: [ "algorithm"]
---

## overview

- 挿入、削除、参照がO(1)
- 衝突に対する実装が必要
  - linked-listを使うなど
  - 衝突が発生すると、O(1+n/m)に増えていく（m:配列の長さ）
  - rehashingはO(n+m)
- keyが変更になった場合の対応に注意
  - 昔のkeyのデータを消して、新しいkeyのデータを挿入する
- keyにはimmutableなものを使う  
 
## bootcamp
ある文字列のリストが与えられたとき、入れ替えると同じ文字になる集合を作る

### brute force solution
- 文字列をソートし、各組み合わせをそれぞれ調べる
- O(n^2 * mlogm) m:うち最大の文字列の長さ

### solution
- ソートした文字をhash tablesに入れていき、各keyごとに出力
- O(nmlogm)

```
def find_anagrams(dictionary):
    sorted_strings = collections.defaultdict(list)
    for s in dictionary:
        sorted_strings[‘’.join(sorted(s))].append(s)
    return [
        group for group in sorted_string.values() if len(group) >= 2
    ]  
```

## hash library
- collections.defaultdict()
- collections.Counter()
- items(), values()

## 12.1 ある文字列が与えられたとき、並び替えることで回文が作れるか？

### brute-force solution
すべての文字列並び替えパターンを作成し、それぞれが回文であるか調べる

### solution
point

- 奇数の長さの文字列でなければ、回文のとき、全てのアルファベットは偶数回出現する
- 文字列の長さが奇数のとき、１つのアルファベットを除いて全てのアルファベットは偶数回出現
- 文字列の長さが偶数のとき、全てのアルファベットは偶数回出現


conclusion

- 各アルファベットの２で割ったあまりを足して、１以下になればよい
- このとき、長さが偶数であれば、必ず０になる
- このとき、長さが奇数であれば、必ず１になる
- 時間計算量：O(n)
- 空間計算量：O(c) cはアルファベットの種類

```
def can_form_pelindrome(s):
    return sum(v%2 for v in collections.Counter(s).values()) <= 1
```
