
#Special. Sum in range
[question](https://www.programmercarl.com/kamacoder/0058.%E5%8C%BA%E9%97%B4%E5%92%8C.html)

The idea for this one is the prefix. More importantly, it introduce an idea of reusing the information we have previosuly. 

If we want to get a specefic result, that would be using certain amount of other arr element, and there is a pattern of them. Then, we could create an new arr to store the information, and reuse it. 

There is a similar leet code question which is calculate an arr, calculate the result that other elements multiply together other than the element itself. It would be similar idea

```python

def solution(arr, ranges):
    prefix = [0] * len(arr)
    cur = 0
    
    for i in range(len(arr)):
        cur+=arr[i]
        prefix[i] = cur
    result = []    
    for k in ranges:
        start = prefix[k[0]]
        end = prefix[k[1]]
        result.append(end-start)
    print(prefix)
    return result
```