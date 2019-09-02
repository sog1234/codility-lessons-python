[Question](https://app.codility.com/programmers/lessons/3-time_complexity/tape_equilibrium/)
Minimize the value |(A[0] + ... + A[P-1]) - (A[P] + ... + A[N-1])|.
```python
def solution(A):
    n = len(A)
    # p = 1
    # left = A[0]
    # right = sum(A) - A[0]
    diff = A[0] * 2 - sum(A)
    diff_abs = abs(diff)
    
    if n == 2:
        return diff_abs
    
    for p in range(2, n):
        # left = left + A[p-1]
        # right = right - A[p-1]
        diff = diff + 2 * A[p-1]
        if abs(diff) < diff_abs:
            diff_abs = abs(diff)
            
    return diff_abs
```