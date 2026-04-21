# 和为k的子数组

给定一个数组nums和一个整数k，要求返回数组中所有和为k的子数组的个数。注意，子数组指的是数组中的连续非空元素序列。

思路：
这道题用到了前缀和的思想：https://leetcode.cn/problems/range-sum-query-immutable/solutions/2693498/qian-zhui-he-ji-qi-kuo-zhan-fu-ti-dan-py-vaar/
使用前缀和进行处理后，问题转化为两数之和，只不过是需要列举所有情况的两数之和。
依旧使用哈希表优化暴力搜索，枚举sj，同时搜索过往是否有sj - k的出现

代码：
```python
from collections import daultdict

s = [0] * (len(nums) + 1) # 初始化前缀和
for i, x in enumerate(nums):
    s[i + 1] = s[i] + x

cnt = daultdict(int) # 当查询一个不存在的key时，返回value为int类型的值，默认为0
ans = 0
for sj in s:
    ans += cnt[sj - k] # sj - si = k, si = sj - k
    cnt[sj] += 1
return ans 
