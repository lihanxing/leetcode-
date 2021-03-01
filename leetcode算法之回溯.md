今天来盘一盘 **回溯 ** 这类题目



使用**python**刷题分类整理的笔记,请参考:  [https://github.com/lxztju/leetcode-algorithm/tree/v1](https://github.com/lxztju/leetcode-algorithm/tree/v1)


## 回溯
**回溯法其实就是暴力法**。经常使用的暴力法就是**多层循环**， 但是面对**树形结构**的话很难采用循环的方式进行遍历。这时就要采用**递归回溯**的方法实现暴力法。

* 17 电话号码的字母组合(medium)


#### 17 电话号码的字母组合(medium)
*用递归的思想解决这个问题
```python
class Solution(object):
    def letterCombinations(self, digits):
        """
        :type digits: str
        :rtype: List[str]
        """
        dic = {
            '2':'abc',
            '3':'def',
            '4':'ghi',
            '5':'jkl',
            '6':'mno',
            '7':'pqrs',
            '8':'tuv',
            '9':'wxyz',
        }
        n = len(digits)
        if n==0:
            return []
        res = []
        def findAlpha(digits,index,s):
            if index==len(digits):
                res.append(s)
                return res
            else:
                digit = digits[index]
                letter = dic[digit]
                for i in range(len(letter)):
                    findAlpha(digits,index+1,s+letter[i])
        findAlpha(digits,0,'')
        return res
```
