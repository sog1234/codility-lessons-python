[Question](https://app.codility.com/programmers/lessons/9-maximum_slice_problem/max_double_slice_sum/)
Find the maximal sum of any double slice.
```python
def solution(A):
    n = len(A)
    
    if n == 3:
        return 0
        
    # let left[i] be max sum of slice ending at i (i > 0)
    # let right[i] be max sum of slice starting at i (i < n-1)
    # then max sum of double slice (x, i, z) is
    # max(right[i+1], left[i-1] + right[i+1], left[i-1], 0)
    # if i = x+1, then sum of double slice is right[i+1]
    # if z = i+1, then sum of double slice is left[i-1]
    # if x+1 = i = z-1, then sum of double slice is 0
    # if x+1 < i < z-1, then sum of double slice is left[i-1] + right[i+1]
    
    # left[i] = max(A[i], left[i-1] + A[i])
    # right[i] = max(A[i], right[i+1] + A[i])
    
    left = [0] * n
    right = [0] * n
    
    # initialization
    left[0] = -1e9-1
    right[n-1] = -1e9-1
    
    for i in range(1, n):
        left[i] = max(A[i], left[i-1] + A[i])
        right[n-i-1] = max(A[n-i-1], right[n-i] + A[n-i-1])
    
    temp_sum = max_sum = -1e9-1
    for i in range(1, n-1):
        temp_sum = max(0, right[i+1], left[i-1] + right[i+1], left[i-1])
        max_sum = max(max_sum, temp_sum)
        
    return max_sum
```