﻿今天来盘一盘 **位运算 ** 这类题目
刷题的笔记来自于https://github.com/lxztju/leetcode-algorithm/blob/master/leetcode%E7%AE%97%E6%B3%95%E4%B9%8B%E4%BD%8D%E8%BF%90%E7%AE%97.md




## 位运算

* 461 汉明距离 (Easy)
* 286 丢失的数字 (Easy)
* 231 2的幂 (Easy)
* 342 4的幂 (Easy)
* 693 交替位二进制数 (Easy)
* 476 数字的补数 (Easy)
* 371 两整数之和 (Easy)

#### 286 丢失的数字 (Easy)
*利用线性方式，求确实数字。
*先对数字进行排序
*看左右两端数字，是否对应为0或n
*在查看数组中元素，前一个加1是否为后一个。是的话继续，否的话返回前一个加1

```python
class Solution(object):
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        n = len(nums)
        nums = sorted(nums)
        if nums[-1] != n:
            return n
        elif nums[0]!=0:
            return 0
        for i in range(n):
            if (nums[i]+1) != nums[i+1]:
                return (nums[i]+1)
```

*利用数学方法求确实数字
*先计算0到n的总和
*再计算数组中的全部和，两者相减为结果


#### 231 2的幂 (Easy)
*用2的幂的性质
*先判断是否为0或1
*再判断是否为奇数，是奇数就return False
*若为偶数就判断是否为2的幂指数
```python
class Solution(object):
    def isPowerOfTwo(self, n):
        """
        :type n: int
        :rtype: bool
        """
        if n==0:
            return False
        elif n==1:
            return True
        while n%2==0:
            n=n/2
            if n==1:
                return True
        return False
```

#### 342 4的幂 (Easy)
*与231的解法一样
```python
class Solution(object):
    def isPowerOfFour(self, n):
        """
        :type n: int
        :rtype: bool
        """
        if n==0:
            return False
        elif n==1:
            return True
        while n%4==0:
            n=n/4
            if n==1:
                return True
        return False
```

#### 693 交替位二进制数 (Easy)
*计算tmp=n^(n>>1)
*再看tmp&(tmp+1)是否为真
```python
class Solution(object):
    def hasAlternatingBits(self, n):
        """
        :type n: int
        :rtype: bool
        """
        tmp = n^(n>>1)
        return tmp&(tmp+1)==0
```

*将n转换为2进制形式，格式为n = bin(n)[2:]
*再判断相邻为是否不同
```python
class Solution(object):
    def hasAlternatingBits(self, n):
        """
        :type n: int
        :rtype: bool
        """
        n = bin(n)[2:]
        for i in range(len(n)-1):
            if n[i]!=n[i+1]:
                continue
            else:
                return False
        return True
```

#### 476 数字的补数 (Easy)
*先用python内置函数bin函数，将十进制数字，转为二进制，用法为:bin(num)[2:]   转换为二进制形式，但为字符串
*再定义新的空字符串，res = ''
*对字符串字符进行判断，字符为1res加0，字符为0res加1
*返回用int('',2)
```python
class Solution(object):
    def findComplement(self, num):
        """
        :type num: int
        :rtype: int
        """
        strs = bin(num)[2:]
        res = ''
        for i in range(len(strs)):
            if strs[i]=='0':
                res+='1'
            elif strs[i]=='1':
                res+='0'
        return int(res,2)
```
#### 371 两整数之和 (Easy)
*直接使用自带函数sum([a,b])
```python
class Solution(object):
    def getSum(self, a, b):
        """
        :type a: int
        :type b: int
        :rtype: int
        """
        return sum([a,b])
```
