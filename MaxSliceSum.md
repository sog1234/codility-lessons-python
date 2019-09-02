[Question](https://app.codility.com/programmers/lessons/9-maximum_slice_problem/max_slice_sum/)
Find a maximum sum of a compact subsequence of array elements.
```python
def solution(A):
    n = len(A)
    
    # let s[i] be the max sum of a slice ending at i
    # then s[i+1] = max(A[i+1], s[i] + A[i+1])
    
    max_sum = temp_sum = -1e6-1
    
    for a in A:
        temp_sum = max(a, temp_sum + a)
        max_sum = max(temp_sum, max_sum)
        
    return max_sum
```