**剑指offer——牛客网**  
=
***
003 重建二叉树
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

```python
class Solution:
    # 返回构造的TreeNode根节点
    def reConstructBinaryTree(self, pre, tin):
        # write code here
        if pre == []:
            return None
        for i in range(len(pre)):
            if tin[i] == pre[0]:
                break
        root = TreeNode(pre[0])
        #cut = tin.index(pre[0])
        root.left = self.reConstructBinaryTree(pre[1:i+1], tin[:i])
        root.right = self.reConstructBinaryTree(pre[i+1:], tin[i+1:])
        return root
```
**NOTE: None 不等同于空list**  
**解题关键：熟悉二叉树遍历定义，前序遍历最先访问根结点，中序遍历访问完左子树，再访问根结点。** 

004 用两个栈实现队列
-
