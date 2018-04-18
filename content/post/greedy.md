---
title: "貪欲法の基礎"
date: 2018-01-29T10:00:00+09:00
tags: [ "algorithm"]
---

## overview
- 各ステップにおいて、局所的な最適な決定を繰り返すソリューション
- 必ずしも最適解を導くわけではない

## bootcamp
- 1,5,10,25,50,100セントを使って、ある金額をできるだけ少ない硬貨で払う

```
def change_making(cents):
  COINS = [100, 50, 25, 10, 5, 1]
  num_coins = 0
  for coin in COINS:
    num_coins += cents // coin
    cents %= coin
  return num_coins
```

## 17.1 Compute an Optimum Assignment of Tasks
- タスクが複数あり、完了までにかかる時間がわかっている。
- １人に対し２つのタスクを割り当てる。１つのタスクが終了したら、次のタスクを実行する
- このとき、すべてのタスクを終了させるのにかかる最短時間を求める

### solution
- sortし、最小と最大の時間がかかるタスクをペアにしていく
- O(nlogn)

```
PairedTasks = collections.namedtuple('PairedTasks', ('task_1', 'task_2'))

def optimum_task_assignment(task_durations):
  task_durations.sort()
  return [
    PairedTasks(task_durations[i], task_durations[~i])
    for i in range(len(task_durations) // 2)
  ]
```
