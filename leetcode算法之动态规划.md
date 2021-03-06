﻿今天来盘一盘 **动态规划 ** 这类题目
 
 ## 动态规划
动规就是**以空间换取时间。**

动态规划常常适用于有**重叠子问题和最优子结构**性质的问题。

一些思考的套路： 递归 （自顶向下）——>  记忆化递归（自顶向下消除重复） ——> 动态规划（自底而上）

1. 菲波那切数列
* 70 爬楼梯 (Easy)
* 198 打家劫舍 (Easy)
* 213 打家劫舍II (Easy)

7. 股票交易
* 121 买卖股票的最佳时机 (Easy)
* 122 买卖股票的最佳时机II (Easy)



1. 斐波那契数列
#### 70 爬楼梯（easy）
*爬到第n阶的方法是第n-1和n-2阶方法之和。
*当爬到n-2阶时，有两种方式，其中一种包含在n-1阶方法中
*所以总的方法是n-1加n-2的方法
*总体就是斐波那契数列
```python
class Solution(object):
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        f = 1
        s = 2
        res = 0
        for i in range(2,n):
            res = f+s
            f=s
            s=res
        return max(n,res)
```

#### 198 打家劫舍 (Easy)
*动态规划方程：dp[n] = MAX( dp[n-1], dp[n-2] + num )
*由于不可以在相邻的房屋闯入，所以在当前位置 n 房屋可盗窃的最大值，要么就是 n-1 房屋可盗窃的最大值，要么就是 n-2 房屋可盗窃的最大值加上当前房屋的值，二者之间取最大值
*举例来说：1 号房间可盗窃最大值为 33 即为 dp[1]=3，2 号房间可盗窃最大值为 44 即为 dp[2]=4，3 号房间自身的值为 22 即为 num=2，那么 dp[3] = MAX( dp[2], dp[1] + num ) = MAX(4, 3+2) = 5，3 号房间可盗窃最大值为 55
```python
class Solution(object):
    def rob(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums:
            return 0
        n = len(nums)
        if n==1:
            return nums[0]
        dp = [0]*n
        dp[0] = nums[0]
        dp[1] = max(nums[0],nums[1])
        for i in range(2,n):
            dp[i] = max(dp[i-2]+nums[i],dp[i-1])
```

#### 213 打家劫舍II (Easy)
*与198类似
*将问题分为两类。1是不偷第一个房间，2是不偷最后一个房间
*解决每一个问题用的都是198的方法
*最后选出最大值
```python
class Solution(object):
    def rob(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums:
            return 0
        n = len(nums)
        if n == 1:
            return nums[0]
        def my_rob(nums):
            n = len(nums)
            if n == 1:
                return nums[0]
            dp = [0]*n
            dp[0] = nums[0]
            dp[1] = max(nums[0],nums[1])
            for i in range(2,n):
                dp[i]=max(dp[i-2]+nums[i],dp[i-1])
            return dp[n-1]
        return max(my_rob(nums[:-1]),my_rob(nums[1:]))
```

7. 股票交易

#### 121 买卖股票的最佳时机 (Easy)

*最简单的方法
*这种方法的时间复杂度太大，为N**2
```python
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        n = len(prices)
        margin = 0
        for i in range(n):
            j=i+1
            while j<n:
                if prices[j]>=prices[i]:
                    margin=max((prices[j]-prices[i]),margin)
                j+=1
        return margin
```

*线性方式
*可以画折线图理解
```python
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        inf = int(1e9)
        minprice = inf
        maxprofit = 0

        for price in prices:
            maxprofit = max(price-minprice,maxprofit)
            minprice = min(price,minprice)
        return maxprofit
```

#### 122 买卖股票的最佳时机II (Easy)
*利用贪心算法
```python
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        n = len(prices)
        ans = 0
        for i in range(1,n):
            tmp = prices[i]-prices[i-1]
            if tmp>0:ans+=tmp
        return ans
```
