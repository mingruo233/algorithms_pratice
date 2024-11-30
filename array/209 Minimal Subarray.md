
# 27 Minimum Size Subarray Sum 
[leetcode](https://leetcode.com/problems/minimum-size-subarray-sum/description/)

A variant of two pointers in my minde - sliding windows. One condition:
1. All positive integers - this gurantee that pops up element will always makes the sum smaller instead of larger

One points to the starting of the subarray and one points to the ending of the subarray, so we we are satisified with the idea that current bis greater than or equal to target, we can start to pop left element to test.


```python
class Solution(object):
    def minSubArrayLen(self, target, nums):
        """
        :type target: int
        :type nums: List[int]
        :rtype: int
        """

        start = 0
        end = 0
        cur= 0
        result = float('inf')
        for end in range(len(nums)): #we including all values [start,end]
            cur+=nums[end]
            while cur>=target and start<=end:
                result = min(result,end-start+1)
                cur-=nums[start]
                start+=1
        
        if result == float('inf'):
            return 0
        else:
            return result
```
