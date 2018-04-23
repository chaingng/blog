---
title: "ビット操作の基礎"
date: 2018-02-05T10:00:00+09:00
tags: [ "algorithm"]
---

## overview
- bit操作に慣れ親しんでおく(特にXOR)
  - `-16 >> 2 == -4`
- maskについて理解する
- 最下位ビットを０にクリアする方法を知る
  - 15 & ~1
- brute-forceでは小さい出力についてキャッシュするのも有効  

## bootcamp
- 整数のビット数を数える
- time O(n) n:number of bits

```
def count_bits(x):
  num_bits = 0
  while x:
    num_bits += x & 1
    x >>= 1
  return num_bits
```

## know primitive types
- sys.maxsize - wordに格納されうる最大の整数を返す
- float('inf'), float('-inf')はintegerの最大・最小値に使える
- math.isclose()はfloatの比較に使える
- randomについて知る
```
>>> import random
>>> random.randrange(28)
16
>>> random.randint(8,28)
25
>>> random.random()
0.7538346882963276
>>> A = [0, 1, 2, 3]
>>> random.shuffle(A)
>>> A
[2, 3, 1, 0]
>>> random.choice(A)
1
```

## 4.1 Computing the parity of a word
- ある文字列のparityを調べる
- ビットの１の数の合計が偶数なら0,奇数なら1を返す

### solution 1
- 1bitずつ順に調べていく
- time O(n) n:number of bits

### solution 2
- X XOR (X-1)が最下位ビットを0にすることを利用する
- time O(k) k: number of 1 bits

### solution 3
- 16ビットまでの結果をキャッシュして、64ビットを16ビットずつ分けて計算してXORをとる
- time O(n/L) L:width of words cached

### solution 4
- 64bitを半分ずつXORしていく
- O(logn)

```
def parity(x):
  x ^= x >> 32
  x ^= x >> 16
  x ^= x >> 8
  x ^= x >> 4
  x ^= x >> 2
  x ^= x >> 1
  return x & 1
```
