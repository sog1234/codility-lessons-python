[Question](https://app.codility.com/programmers/lessons/17-dynamic_programming/min_abs_sum/)
Given array of integers, find the lowest absolute sum of elements.
```python
def solution(A):
    # time complexity: O(n^2 * max(A))

    if not A:
        return 0

    # by the hint of the official solution
    # it is a 0-1 Knapsack problem

    # goal: find largest P <= S//2
    
    A = [abs(a) for a in A if a != 0]

    sumA = sum(A)
    half = sumA // 2

    n = len(A)
    p = [0] * (half + 1)
    
    # p[i][j] is the max sum that is <= j 
    # and chosen from A[0] ... A[i] 

    for j in range(A[0], half+1):
        p[j] = A[0]

    for i in range(1, n):
        for j in range(half, A[i]-1, -1):
            p[j] = max(p[j], p[j - A[i]] + A[i])

    return sumA - 2 * p[half]
```
