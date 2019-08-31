[Question](https://app.codility.com/programmers/lessons/15-caterpillar_method/count_triangles/)

```python
def solution(A):
    A.sort()
    n = len(A)
    
    if n < 3:
        return 0
    
    count = 0
    for p in range(n-2):
        r = p + 2
        for q in range(p+1, n-1):
            # now A is sorted 
            # only need to check on inequality
            while r < n and A[p] + A[q] > A[r]:
                r += 1
                
            count += r-q-1
            
    return count
```