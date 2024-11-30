
# 704 Binary Search
[leetcode](https://leetcode.com/problems/binary-search/)

I just did this leetcode recently so it wasn't really hard to code. Put the solutions below. Personally I prefer [left,right], as we operate on left and right with the same logics.

One question I was having with [left,right) is, I accidentally put right = mid when the value is smallest is target - I believe my original thought is since it is smaller, we want to move to the left side. I twould be more helpful to actually draw the picture next time


### Python [left,right]

```python
class Solution(object):
    def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        left=0
        right=len(nums)-1
        while(left<=right): #[left,right) the actual range is [left,right-1] 
            mid=(left+right)//2
            if(nums[mid]==target):
                return mid
            elif (nums[mid]<target):
                left=mid+1
            else:
                right=mid-1
        return -1

```
### Python [left,right)
```python
class Solution(object):
    def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        left=0
        right=len(nums)
        while(left<right): #[left,right) the actual range is [left,right-1] 
            mid=(left+right)//2
            if(nums[mid]==target):
                return mid
            elif (nums[mid]<target):
                left=mid+1
            else:
                right=mid
        return -1
```



