---
title: "ヒープの基礎"
date: 2017-12-10T10:00:00+09:00
tags: [ "algorithm"]
---

## 概要
- ヒープは特別な二分木
- 完全二分木である
- 親ノードの値は子よりも小さい（最小ヒープのとき）
- 配列で実装できる。親iの子は2i+1, 2i+2
- 挿入と削除がO(logn)、最小値の参照がO(1)
- priority queueのようにも参照される。違いは必ず最大優先度のノードが削除されること

## 10.1 ソートされたリストの統合
- 入力：<3,5,7> <0,6> <0,6,28> 
- 出力:<0,0,3,5,6,6,7,28>

### brute-force
- すべて連結してからソート
- time O(nlogn)

### best solution
- k: number of input sequences
- space O(k)
- time O(nlogk)
  - insert O(logk) x for all element n
  
```
  def merge_sorted_arrays(sorted_arrays):
    min_heap = []
    sorted_arrays_iters = [iter(x) for x in sorted_arrays]
    
    for i, it in enumerate(sorted_arrays_iters)
      first_element = next(it, None)
      if first_element is not None:
        heapq.heappush(min_heap, (first_element, i))
    
    result = []
    while min_heap:
      smallest_entry, smallest_array_i = heapq.heappop(min_heap)
      smallest_array_iter = sorted_arrays_iters[smallest_array_i]
      result.append(smallest_entry)
      next_element = next(smallest_array_iter, None)
      if next_element is not None:
        heapq.heappush(min_heap, (next_elelement, smalletst_array_i))
    return result
    
```
