今天来盘一盘 **贪心算法 ** 这类题目



使用**python**刷题分类整理的笔记,请参考:  [https://github.com/lxztju/leetcode-algorithm/tree/v1](https://github.com/lxztju/leetcode-algorithm/tree/v1)

## 贪心算法
贪心算法是指每步都选择最优的策略，以此达到全局的最优。**局部最优—>全局最优**

贪心策略的选择必须具备**无后效性**，也就是说某个状态以前的过程不会影响以后的状态，只与当前状态有关。

* 455 分发饼干  (Easy)
* 665 非递减数列 (Easy)
* 53 最大子序和 (Easy)




#### 455 分发饼干  (Easy)
* 采用贪心策略
*对胃口数组和饼干数组进行排序
*所以这道题我们可以让胃口大的吃大块，胃口小的吃小块。

*一种最简单的方式就是先从胃口最小的孩子开始，拿最小的饼干试一下能不能满足他，如果能满足就更好，如果不能满足，在找稍微大一点的，如果还不能满足就再找更大一点的……

```python
class Solution(object):
    def findContentChildren(self, g, s):
        """
        :type g: List[int]
        :type s: List[int]
        :rtype: int
        """
        n,m = len(g),len(s)
        count = 0
        g,s= sorted(g),sorted(s)
        i,j = 0,0
        while i<n and j<m:
            while j<m and s[j]<g[i]:
                j+=1
            if j<m:
                count+=1
                j+=1
            i+=1
        return count
```

#### 665 非递减数列 (Easy)
*使用贪心算法
*定义一个标志，这个标志只能变换一次，变换后代表着return False
*使用瞻前顾后的思想.
```python
class Solution(object):
    def checkPossibility(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        n = len(nums)
        flag = True
        for i in range(n-1):
            if nums[i]>nums[i+1]:
                if flag == False:
                    return False
                if i == 0 or nums[i+1]>=nums[i-1]:
                    nums[i] = nums[i+1]
                else:
                    nums[i+1] = nums[i]
                flag = False
        return True

```

#### 53 最大子序和 (Easy)
