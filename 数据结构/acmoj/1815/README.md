# 1815. 导弹拦截

首先翻译成人话：找到 $Δx$ 最小的两个元素使 $Δy≥D$。

## Brute Force

遍历 ij。TLE。源码 [`brute_force.cpp`](./brute_force.cpp)

## 半 Brute Force：排序 x +剪枝

先通过最大/最小 y 处理无解情况，并获得一个也许不错的 delta x 后，排序 x 再遍历 ij。

剪枝的策略如下：
- 去掉 delta x > 当前值的情况

## x map

题目明确提示了：x 不重复。因此可以做一个简单的 x-y map。

## 最坏情况
- [(1, 2), (2, 1), (3, 3), (5, 4)]
- 重复 y 的
- 密度高、近线性的
- 无解的
- 