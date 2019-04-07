**剑指offer——牛客网**  
=
***
007 重建二叉树
-
```python
# -*- coding:utf-8 -*-
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution:
    # 返回构造的TreeNode根节点
    def reConstructBinaryTree(self, pre, tin):
        # write code here
        if pre == []:     
            return None
        root = TreeNode(pre[0])
        cut = tin.index(pre[0])
        root.left = self.reConstructBinaryTree(pre[1:cut+1], tin[:cut])
        root.right = self.reConstructBinaryTree(pre[cut+1:], tin[cut+1:])
        return root
```
**NOTE: None 不等同于空list**
