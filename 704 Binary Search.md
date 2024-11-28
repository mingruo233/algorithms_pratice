
#704 Binary Search
[leetcode](https://leetcode.com/problems/binary-search/)

I just did this leetcode recently so it wasn't really hard to code


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

