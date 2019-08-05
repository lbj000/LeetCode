在未排序的数组中找到第 k 个最大的元素。请注意，你需要找的是数组排序后的第 k 个最大的元素，而不是第 k 个不同的元素。

示例 1:  

输入: [3,2,1,5,6,4] 和 k = 2  
输出: 5  
示例 2:  
  
输入: [3,2,3,1,2,4,5,5,6] 和 k = 4  
输出: 4  

class Solution:

    def findKthLargest(self, nums: List[int], k: int) -> int:
        nums.sort()
        nums.reverse()
        return nums[k-1]
        
一开始，不知道python内置的堆模块，自己又不想写，就试着排序，虽然通过但并不是最好的解决方法，所以查阅heapq库使用后，改用堆实现  

import heapq  
class Solution:
    
    def findKthLargest(self, nums: List[int], k: int) -> int:
        heap = []
        for i in range(k):
            heapq.heappush(heap,nums[i])
        for i in range(k,len(nums)):
            if heap[0] < nums[i]:
                heapq.heappop(heap)
                heapq.heappush(heap,nums[i])
        return heap[0]
