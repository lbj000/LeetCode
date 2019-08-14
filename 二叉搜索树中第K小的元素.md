给定一个二叉搜索树，编写一个函数 kthSmallest 来查找其中第 k 个最小的元素。

说明：
你可以假设 k 总是有效的，1 ≤ k ≤ 二叉搜索树元素个数。

示例 1:

  输入: root = [3,1,4,null,2], k = 1  

   3  
   /  \  
1    4  
   \  
    2  
   
输出: 1  

示例 2:

输入: root = [5,3,6,2,4,null,null,1], k = 3  

        5  
       / \  
       3   6  
     / \  
    2  4  
    /  
  1  
 
输出: 3

// Definition for a binary tree node.  
// class TreeNode:  
//     def __init__(self, x):  
//         self.val = x  
//         self.left = None  
//         self.right = None  

class Solution:

    l = []
    def kthSmallest(self, root: TreeNode, k: int) -> int:
        self.l =[]
        i = self.biLi(root)
        print(heapq.nsmallest(k, i)[-1])
        
        return heapq.nsmallest(k, i)[-1]
    def biLi(self,r:TreeNode):
        while r:
            self.l.append(r.val)
            self.biLi(r.left) 
            self.biLi(r.right)
            return self.l
