# 2183. 与众不同

本题看起来十分复杂：又是“最长不重复序列”，又是区间查询，好在数据不需要修改。

通过动态规划我们可以在 O(n) 时间内获得“以 `i` 位置结束的最长序列起始位置”的列表 `starts`。
然后可以通过遍历 $[L,R]$ 区间，最大长度为 `max_i(i-max(L, starts[i]))+1`，时间复杂度为 O(R-L)。

这个查询显然过于耗时，我们需要一个对数时间的区间查询算法。

问题的关键在于这个算法中，对于不同的 i 要分别计算 `i-max(...)`，故不能分块优化。

遂 Google，答案是，由于“最长不重复序列”的左边界、右边界序列都具有单调性，可以把 [L,R] 分成
两部分：前一部分的起始位置 <L，最大值为临界点-L，后一部分的起始位置 >=L；最大值为 max(i-starts[i])，
这可以通过维护线段树 maxlen[i] 进行 O(log(n)log(R-L)) 查询。分界点可以通过二分 O(log(R-L)) 时间内找到。

