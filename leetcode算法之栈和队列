今天来盘一盘 **栈以及队列 ** 这两类题目



使用**python**刷题分类整理的笔记,请参考:  [https://github.com/lxztju/leetcode-algorithm/tree/v1](https://github.com/lxztju/leetcode-algorithm/tree/v1)

## 栈和队列

> **栈: 先进先出 
> 队列: 先进后出**

利用这两类数据结构的特性解题.

其中一类非常经典的题目是: **单调栈(leetcode496题, 经典题目)**. 

* **单调递减栈**, 是指针对每一个待遍历的元素x, 将x与栈顶元素相比, 如果大于栈顶元素将栈顶元素出栈, 重新循环对比,直到小于栈顶元素,然后将x入栈. 
* **单调递增栈**: 同理分析

---

* 232 用栈实现队列 (Easy)
* 225 用队列实现栈 (Easy)
* 155 最小栈 (Easy)
* 1021 删除最外层的括号 (Easy)
* 496 下一个更大的元素 (Easy)


####  232 用栈实现队列 (Easy)
*python定义类
*使用两个栈实现这一操作
*push为入队列操作
*pop为出队列操作，在这个操作中进行汉诺塔操作
*peek返回队列头顶元素
```python
class MyQueue(object):

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.stack1=[]
        self.stack2 = []


    def push(self, x):
        """
        Push element x to the back of queue.
        :type x: int
        :rtype: None
        """
        """
        while self.stack1:
            self.stack2.append(self.stack1.pop())
        """
        self.stack1.append(x)  
        """
        while self.stack2:
            self.stack1.append(self.stack2.pop())
        """      

    def pop(self):
        """
        Removes the element from in front of queue and returns that element.
        :rtype: int
        """
        while self.stack1:
            self.stack2.append(self.stack1.pop())
        a = self.stack2.pop()
        while self.stack2:
            self.stack1.append(self.stack2.pop())
        return a

    def peek(self):
        """
        Get the front element.
        :rtype: int
        """   
        return self.stack1[0]
     


    def empty(self):
        """
        Returns whether the queue is empty.
        :rtype: bool
        """
        return not self.stack1
```

####  225 用队列实现栈 (Easy)
```python
class MyStack(object):

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.dui1=[]
        self.dui2=[]

    def push(self, x):
        """
        Push element x onto stack.
        :type x: int
        :rtype: None
        """
        self.dui1.append(x)

    def pop(self):
        """
        Removes the element on top of the stack and returns that element.
        :rtype: int
        """
        return self.dui1.pop()


    def top(self):
        """
        Get the top element.
        :rtype: int
        """
        return self.dui1[-1]


    def empty(self):
        """
        Returns whether the stack is empty.
        :rtype: bool
        """
        return not self.dui1
```

####  155 最小栈 (Easy)
```python
class MinStack(object):

    def __init__(self):
        """
        initialize your data structure here.
        """
        self.stack=[]


    def push(self, x):
        """
        :type x: int
        :rtype: None
        """
        self.stack.append(x)


    def pop(self):
        """
        :rtype: None
        """
        if self.stack:
            return self.stack.pop()
        else:
            return None

    def top(self):
        """
        :rtype: int
        """
        if self.stack:
           a = self.stack[-1]
           return a
        else:
            return None


    def getMin(self):
        """
        :rtype: int
        """
        if self.stack:
            return min(self.stack)
        else:
            return None
```

#### 1021 删除最外层的括号 (Easy)
*用一个栈就好
*当遇到(时进站
*当遇到)时出栈
*当栈为空时，说明一个大括号判断完毕
```python
class Solution(object):
    def removeOuterParentheses(self, S):
        """
        :type S: str
        :rtype: str
        """
        res,stack="",[]
        for c in S:
            if c=='(':
                if stack: res+=c
                stack.append(c)
            elif c==')':
                stack.pop()++
                if stack: res+=c
        return res
```

#### 496 下一个更大的元素 (Easy)
*暴力解决
```python
class Solution(object):
    def nextGreaterElement(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        #nums1的长度
        len1 = len(nums1)

        result = []

        for i in nums1:
            for j in range(len2):
                if nums2[j]==i:
                    k = j+1
                    ans = 0
                    while k<len2:
                        if nums2[k]>i:
                            ans = 1
                            result.append(nums2[k])
                            break
                        k+=1
                    if ans==0:
                        result.append(-1)
                    
        return result
```

*单调栈
```python
class Solution(object):
    def nextGreaterElement(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        stack = []
        hashmap = {}
        result = []
        for i in nums2:
            #这里是一直循环，[6,5,4,3,2,1,7]中，7是最后一位
            #当7进入后，栈中元素会依次到达栈顶与7比较，在这过程中循环持续进行
            while stack and stack[-1]<i:
                hashmap[stack.pop()] = i
            stack.append(i)
        while stack:
            hashmap[stack.pop()]=-1
        for i in nums1:
            result.append(hashmap[i])
        return result

```
