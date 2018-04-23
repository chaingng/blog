---
title: "二分木の基礎"
date: 2017-12-10T10:00:00+09:00
tags: [ "algorithm"]
---

## 概要
- 空であるか、左の二分木の子と右の二分木の子をもつroot nodeがある木
- 二分探索木としてのコンテキストでよく現れる
- すべての木をたどるにはO(n)time, O(h)space
- 木には再帰が有効であることがある
- nodeに親の参照があれば、timeとspaceを減らすことができる

## 二分木の実装

```
def BinaryTreeNode:
  def __init__(self, data=None, left=None, right=None):
    self.data = data
    self.left = left
    self.right = right
```

## 9.1 二分木が平衡であるか判定
- 左と右の部分木の高さの差が１以内であるとき、平衡
- O(h)space, O(n)time

```
def is_balanced_binary_tree(tree):
  BalancedStatusWithHeight = collections.namedtuple('BalancedStatusWithHeight', ('balanced', 'height'))
  
  def check_balanced(tree):
    if not tree:
      return BalancedStatusWithHeight(True, -1)
      
    left_result = check_balanced(tree.left)
    if not left_result.balanced:
      return BalancedStatusWithHeight(False, 0)
      
    right_result = check_balanced(tree.right)
    if not right_result.balanced:
      return BalancedStatusWithHeight(False, 0)
      
    is_balanced = abs(left_result.height - left_result.height) <= 1
    height = max(left_result.height - left_result.height) + 1
    return BalancedStatusWithHeight(is_balanced, height)
    
   return check_balanced(tree).balanced   
```
