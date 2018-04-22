---
title: "連結リストの概要"
date: 2017-12-31T10:00:00+09:00
tags: [ "algorithm"]
---

## 概要
- 挿入と削除がO(1)
- k番目の要素の取得がO(n)
- nodeはdata, nextフィールドを持つ
- dummy headを設けることで空のリストかのチェックがいらなくなる
- 2つのイテレータをもつ解法が有効なことがある

## 7.1 ２つのソート済み配列のマージ
- time O(n+m)
- space O(1) if reuse the existing nodes

```
def merge_two_sorted_lists(L1, L2):
    dummy_head = tail = ListNode()
    while L1 and L2:
        if L1.data < L2.data:
            tail.next, L1 = L1, L1.next
        else:
            tail.next, L2 = L2, L2.next

    tail.next = L1 or L2
    return dummy_head.next
```
