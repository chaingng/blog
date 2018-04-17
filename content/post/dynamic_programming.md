---
title: "動的計画法の基礎"
date: 2018-01-22T10:00:00+09:00
tags: [ "algorithm"]
---

## overview
- DPはいつでも解法の１つになりえる
- 特にサブ問題に関連する問題に適用できる
- 分割統治との違いは、同じサブ問題が何度も起こり得ること。そのため、cacheが有効
- 枝刈りを行う場合などは、再帰のほうが適している可能性がある

## bootcamp
- fibonacci関数
- time O(n), space O(1)

```
def fibonacchi(n):
  if n <= 1:
    return n
    
  f_minus_2, f_minus_1 = 0, 1
  for _ in range(1,n):
    f = f_minus_2 + f_minus_1
    f_minus_2, f_minus_1 = f_minus_1, f
  
  return f_minus_1
```

- 数字の配列があり、もっとも和が大きくなるサブ配列を求める
- 単にそれまでの最大をもっていてもダメ
- それまでの最小と最大をもち、更新していく

```
def find_maximum_subarray(A):
  min_sum = max_sum = 0
  
  for current_sum in itertools.accumulate(A):
    min_sum = min(min_sum, running_sum)
    max_sum = max(max_sum, running_sum - min_sum)
    
 return max_sum
```

## 16.1 Count The Number Of Score Combinations
- アメリカンフットボールゲームで、2points, 3points, 7pointsの得点がある
- ある合計得点について、その点になるすべての組み合わせ数を求める
- time O(n^2) space(ns) s:number of point pattern

```
def num_combinations_for_final_score(final_score, individual_play_scores):
  num_combinations_for_score = [[1]+[0]*final_score for _ in individual_play_scores]
  for i in range(1, final_score+1):
    without_this_play = (num_combinations_for_score[i-1][j] if i>=1 else 0)
    with_this_play = (num_combinations_for_score[i][j - individual_play_scores[i]] if j>=individual_play_scores[i] else 0)
    num_combinations_for_score[i][j] = (without_this_play + with_this_play)
    
  return num_combination_for_score[-1][-1]
```
