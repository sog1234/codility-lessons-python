[Question](https://app.codility.com/programmers/lessons/6-sorting/triangle/)
Determine whether a triangle can be built from a given set of edges.
```python
def solution(A):
    n = len(A)
    
    if n < 3:
        return 0
        
    A.sort()
    
    # then only need to check one inequality
    # i.e., if the sum of the smallest two is big than the largest
    # also note that the smallest can not be less than 1
    # thus, all of them have to be positive
    
    pos = -1
    
    for i in range(n):
        if A[i] > 0:
            pos = i
            break
        
    if pos == -1 or (n-pos) < 3:
        return 0
        
    # then there are at least 3 positive integers
    # note that only need to check if (i, j, j+1) are triangular
    
    for i in range(n-2):
        for j in range(i+1, n-1):
            if A[i] > (A[j+1] - A[j]):
                return 1
                
    return 0
```