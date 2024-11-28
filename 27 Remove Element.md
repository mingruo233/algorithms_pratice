
#27 Remove Element
[leetcode](https://leetcode.com/problems/remove-element/description/)

I actually like two pointers for some reasons.
Anywa, looking at the problem, firstly it have some conditions:
1. We need move in place 
2. we only need k elements, which means we have len(nums) - k space to store something that we dont use, which in this case, the first intution is the target element

Previously thinking of this question, I am trapped to find the value, and kinda mixed it. However, looking back to the result **What is the final output we want it to be?**

we want a new array (kinda) with no val.

Instead of thinking to find the val itself, lets find the values that is not val - which means it is the element of new array.

Then the idea is simple, find new element, keep it. Then the answer should pops pretty soon:
slow - tracks the space of new array (i.e next available slot for the new array)
fast - find the good element. If it is good, slow takes it and slow move to the next available. If it is bad, skip it because there are two cases:
1. If it is outside of k, we dont care it
2. If it is inside of k, it will become an available slot, which means slow will points to it eventually and good value will takes place of it
### Python [left,right]

```python
class Solution(object):
    def removeElement(self, nums, val):
        """
        :type nums: List[int]
        :type val: int
        :rtype: int
        """
        #in place
        #anything after k isnt important
        #slow represents the new array
        #fast finds the next good element
        slow = 0
        
        for fast in range(len(nums)):
            if nums[fast]!=val:
                nums[slow]=nums[fast]
                slow+=1
            fast+=1
        return slow 
```
