今天来盘一盘 **递归 ** 这类题目

这类题目是我一直很头疼的题目, 感觉有点难, 从这篇文章开始,就要开始比较难的一部分了

使用**python**刷题分类整理的笔记,请参考:  [https://github.com/lxztju/leetcode-algorithm/tree/v1](https://github.com/lxztju/leetcode-algorithm/tree/v1)

## 递归
* 104 二叉树的最大深度  (Easy)
* 110 平衡二叉树 (Easy)


#### 104 二叉树的最大深度  (Easy)
*使用递归的思想
*令左右子树的层数为l，r，返两者的最大值，然后再加1(根节点)
```python
class Solution(object):
    def maxDepth(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        if root == None:
            return 0
        else:
            left_count = self.maxDepth(root.left)
            right_count = self.maxDepth(root.right)
            return max(left_count,right_count)+1
```

#### 110 平衡二叉树 (Easy)
*我自己做的错误版本
```python
class Solution:
    def isBalanced(self, root):

        def height_max(root):
            if root==None:
                return 0
            else:
                left_count = height_max(root.left)
                right_count = height_max(root.right)
                return max(left_count,right_count)+1
        
        def height_min(root):
            if root==None:
                return 0
            else:
                left_count = height_min(root.left)
                right_count = height_min(root.right)
                return min(left_count,right_count)+1


        if root == None:
            return True
        
        left_count_max = height_max(root.left)+1
        right_count_max = height_max(root.right)+1
        left_count_min = height_min(root.left)+1
        right_count_min = height_min(root.right)+1

        print(left_count_max,left_count_min,right_count_max,right_count_min)
        return abs(left_count_max-left_count_min) <= 1 and abs(right_count_max-right_count_min)<=1
```
*正确版本1
```python
class Solution:
    def isBalanced(self, root):
        self.res = True
        def height(root):
            if root == None:
                return 0
            left = height(root.left)+1
            right = height(root.right)+1
            if abs(left-right)>1:
                self.res = False
            return max(left,right)
        
        height(root)
        return self.res
```
*正确版本2
```python
class Solution(object):
    def isBalanced(self, root):
        if not root:
            return True
        return self.isBalanced(root.left) and self.isBalanced(root.right) and abs(self.getheight(root.left)-self.getheight(root.right))<=1

    def getheight(self,root):
        if not root:
            return 0
        return max(self.getheight(root.left),self.getheight(root.right))+1
```
