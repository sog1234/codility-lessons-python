[Question](https://app.codility.com/programmers/lessons/8-leader/dominator/)

```python
def solution(A):
    n = len(A)
    
    if n == 0:
        return -1
    
    # index for dominator   
    index = 0
    count = 0
    
    size = 0
    for i in range(n):
        # if the stack is empty
        if size == 0:
            val = A[i]
            size += 1
        else:
            if val == A[i]:
                size += 1
            else:
                size -= 1
    
    if size == 0:
        return -1
    
    for i in range(n):
        if A[i] == val:
            index = i
            count += 1
    
    if count > n // 2:
        return index
    else:
        return -1
```