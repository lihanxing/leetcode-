今天来盘一盘 **递归 ** 这类题目

这类题目是我一直很头疼的题目, 感觉有点难, 从这篇文章开始,就要开始比较难的一部分了

使用**python**刷题分类整理的笔记,请参考:  [https://github.com/lxztju/leetcode-algorithm/tree/v1](https://github.com/lxztju/leetcode-algorithm/tree/v1)

## 递归
* 104 二叉树的最大深度  (Easy)


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
