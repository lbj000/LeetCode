合并 k 个排序链表，返回合并后的排序链表。请分析和描述算法的复杂度。

示例:

输入:  
[  
  1->4->5,  
  1->3->4,  
  2->6  
]  
输出: 1->1->2->3->4->4->5->6  

/# Definition for singly-linked list.  
/# class ListNode:  
/#     def __init__(self, x):  
/#         self.val = x  
/#         self.next = None  

class Solution:

    def mergeKLists(self, lists: List[ListNode]) -> ListNode:
        ln = lnd = ListNode(0)
        # lnd = ListNode(0)
        l = []
        for i in lists:
            while i.next != None:
                l.append(i.val)
                i = i.next
            l.append(i.val)
        l.sort()
        for i in l:
            lnd.next = ListNode(i)
            lnd = lnd.next
        return(ln.next)

参考别人代码，实现最后的返回
