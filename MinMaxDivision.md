[Question](https://app.codility.com/programmers/lessons/14-binary_search_algorithm/min_max_division/)
Divide array A into K blocks and minimize the largest sum of any block.
```python
# given a large sum
# check if number of actual blocks is less than k
def check(A, k, large_sum):
    blocks = 1
    block_sum = 0
    
    for a in A:
        if (block_sum + a) > large_sum:
            blocks += 1
            if blocks > k:
                return 0
            block_sum = a
        else:
            block_sum += a
    
    return 1
    
    
def solution(k, m, A):
    n = len(A)
    
    # large sum is between max(A) and (n // k + 1) * m
    lo = max(A)
    hi = (n // k + 1) * m
    large_sum = -1
    while lo <= hi:
        mid = (lo + hi) // 2
        if check(A, k, mid):
            hi = mid - 1
            large_sum = mid
        else:
            lo = mid + 1
    
    return large_sum
```