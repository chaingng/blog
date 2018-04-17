---
title: "再帰の基礎"
date: 2018-01-22T10:00:00+09:00
tags: [ "algorithm"]
---

## overview
- 部分的により小さいソリューションに分解できる問題
- 検索、列挙、分割統治、複雑な問題の分解は再帰を適用できる可能性がある
- 再帰関数はベースケースと、同じ関数を異なる引数で呼び出すことで構成される
- ベースケースを明らかにすることと、そこからソリューションに至るプロセスを確認することが解くために大事
- 入力が再帰を使って表現できるとき、特に適している
- 再帰は検索、列挙、分割統治に対してよい選択肢
- 同じ引数が現れるときはcacheが有効

## bootcamp
- GCDを求める
- GCD(y,x) == GCD(x, y-x)
- time O(n) n: number of bits
- space O(n)

## 15.1 The Towers of Hanoi Problem
- P0にすべての塔があり、P1,P2は空。P1にすべて移したい
- 一番下以外をP2に移し、一番下をP1に移す。その後、P2のものをP1に移す
- time O(2^n)

```
def compute_tower_hanoi(num_strings):
  def compute_tower_hanoi_steps(num_rings_to_move, from_peg, to_peg, use_peg):
    if num_rings_to_move > 0:
      compute_tower_hanoi_steps(num_rings_to_move-1, from_peg, use_peg, to_peg)
      peg[to_peg].append(pegs[from_peg].pop())
      result.append([from_peg, to_peg])
      compute_tower_hanoi_steps(num_rings_to_move-1, use_peg, to_peg, from_peg)

  result = []
  pegs = [list(reversed(range(1, num_rings+1)))] + [[] for _ in range(1, NUM_PEGS)]
  compute_tower_hanoi_steps(num_rings, 0, 1, 2)
  return result
```
