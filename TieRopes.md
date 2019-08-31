[Question](https://app.codility.com/programmers/lessons/16-greedy_algorithms/tie_ropes/)

```python
def solution(K, A):
    n = len(A)
    
    # if sum of two adjacent ropes is less than K
    # tie them together
    # it's easy to prove this gives an optimal solution
    
    length = 0
    count = 0
    
    for i in range(n):
        if length + A[i] < K:
            length += A[i]
        else:
            count += 1
            length = 0
    
    return count
```