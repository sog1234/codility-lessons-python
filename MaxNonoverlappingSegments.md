[Question](https://app.codility.com/programmers/lessons/16-greedy_algorithms/max_nonoverlapping_segments/)
Find a maximal set of non-overlapping segments.
```python
def solution(A, B):
    n = len(A)
    
    # since B is non-decreasing
    # so as long as the segment is not overlapping with
    # the last one in the set, select it
    # again it's easy to prove this gives an optimal solution
    
    end = -1
    count = 0
    
    for i in range(n):
        if A[i] > end:
            count += 1
            end = B[i]
            
    return count
```