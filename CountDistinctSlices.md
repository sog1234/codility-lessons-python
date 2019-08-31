[Question](https://app.codility.com/programmers/lessons/15-caterpillar_method/count_distinct_slices/)

```python
def solution(m, A):
    n = len(A)
    
    # use count array to save the occurrences
    count = [0] * (m+1)
    # store number of distinct slices
    num, q = 0, 0
    for p in range(n):
        while q < n and count[A[q]] == 0:
            # update count
            count[A[q]] = 1
            q += 1
        # A[p] to A[q-1] are distinct
        num += (q - p)
        if num > 1000000000:
            return 1000000000
        # update count
        count[A[p]] = 0
        
    return num
```