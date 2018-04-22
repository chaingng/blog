---
title: "二分探索木の基礎"
date: 2017-12-17T10:00:00+09:00
tags: [ "algorithm"]
---

## 概要
- keyを効率良く探すことができ、かつmin/maxも同様に効率的に探せる
- keyの範囲も探すことができる
- ソートされた配列と似ているが、keyの挿入と削除が効率的に行える
- あるkeyの左側の木のノードはすべてkey以下で、右側の木のノードはすべてkey以上になる
- 木が偏っていると挿入と削除はO(n)になるが、高さのバランスが取れた木はO(logn)となる
- 赤黒木はバランスのとれた木のひとつ
- ソート済みの要素をO(n)でイテレートできる
- 二分探索木とハッシュテーブルの組み合わせが有効な問題もある

## 二分探索木の実装
```
class BstNode:
  def __init__(self, data=None, left=None, right=None):
    self.data, self.left, self.right = data, left, right
```

## 二分探索木の探索
```
def search_bst(tree, key):
  return (
    tree if not tree or tree.data == key else search_bst(tree.left, key)
    if key < tree.data else search_bst(tree.right, key))
  )
```

## 14.1 二分木が二分探索木の条件を満たすかどうか
```
def is_binary_tree_bst(tree):
  QueueEntry = collections.namedtuple('QueueEntry', ('node', 'lower', 'upper'))
  
  bfs_queue = collections.deque([QueueEntry(tree, float('-inf'), float('inf'))])
  
  while bfs_queue:
    front = bfs_queue.popleft()
    if front.node:
      if not front.lower <= front.node.data <= front.upper:
        return False
       bfs_queue += [
        QueueEntry(front.node.left, front.lower, front.node.data),
        QueueEntry(front.node.right, front.node.data, front.upper)
       ]
  return True
```
