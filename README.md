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
```python
-*- coding:utf-8 -*-
class Solution:
    def __init__(self):
        self.stack1 = []
        self.stack2 = []
    def push(self, node):
        # write code here
        self.stack1.append(node)
    def pop(self):
        # return xx
        if self.stack2 != []:
            return self.stack2.pop()
        if self.stack1 == []:
            return None
        while self.stack1 != []:
            self.stack2.append(self.stack1.pop())
        return self.stack2.pop()  #pop()自带对空list的处理
```
**解题思路：栈和队列的区别只在pop的时候有所体现，因此对删除元素的几种情形进行画图举例，即可得出解题思路。**  

005 旋转数组的最小数字
-
```python
# -*- coding:utf-8 -*-
class Solution:
    def minNumberInRotateArray(self, rarray):
        # write code here
        if rarray == []:
            return 0
        l = 0
        r = len(rarray) - 1
        if rarray[l] < rarray[r]:
            return rarray[0]
        while (r-l) > 1:
            mid = (l+r)/2
            if (rarray[l] == rarray[r]) & (rarray[mid] == rarray[l]):
                return self.minarray(rarray[l,r])
            if rarray[mid] >= rarray[l]:
                l = mid
            else:
                r = mid
        return rarray[r]
    def minarray(self, array):
        m = array[0]
        for i in array:
            if i < m:
                m = i
        return m
```
**解题关键：类排序数组联想到二分查找，再举例分析查找过程中的各种情形，形成思路。**    

00
-
```python

```
****  

00
-
```python

```
****  

00
-
```python

```
****  

00
-
```python

```
****  

00
-
```python

```
****  

00
-
```python

```
****  
