
# pecial. Minimal Difference in matrix.md
[question](https://www.programmercarl.com/kamacoder/0058.%E5%8C%BA%E9%97%B4%E5%92%8C.html)

I was a bit not confident when doing the problem, have to double check the correct answer partially to ensure I am on the right page.
Next time, I would set a timer of 15 mins for myself before looking the answer.

The key ideas is recognize that the cells can only be divided horizontally of vertically. Consider this, there are two cases:
1. Horizontally: Then there first part is all the sum row[0] to row[i], the second part os row[i+1] to row[n]
2. Vertically: Then the first part is all the sum col[0] to col[i], the second part is col[i+1] to col[n]

Therefore, we will need 2 prefix sum array. One record the the cumulative sum of col and one record the cumulative sum of row... here it looks like I did not cumulative, but still works, and does not affect the time complexity would be O(n*m)



##python
```python

def solution(arr):
    n = len(arr)
    m = len(arr[0])
    horizontal = [0]*n
    total = 0
    vertical = [0]*m
    
    for i in range(n):
        cur = 0
        for j in range(m):
            cur+=arr[i][j]
        horizontal[i]=cur
        total+=cur
    
    for k in range(m):
        cur = 0
        for i in range(n):
            cur+=arr[i][j]
        vertical[k]=cur
    
    min_difference = float("inf")
    
    horizontal_upper = 0
    horizontal_total = total
    for i in range(n-1):
        horizontal_upper+=horizontal[i]
        horizontal_total-=horizontal[i]
        min_difference = min(abs(horizontal_total-horizontal_upper),min_difference)
    vertical_left = 0
    vertical_total = total
    for k in range(m-1):
        vertical_left+=vertical[k]
        vertical_total-=vertical[k]
        min_difference = min(abs(vertical_total-vertical_left),min_difference)
        
    return min_difference
```