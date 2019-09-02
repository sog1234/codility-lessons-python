[Question](https://app.codility.com/programmers/lessons/3-time_complexity/perm_missing_elem/)
Find the missing element in a given permutation.
```python
def solution(A):
    n = len(A)
    
    if n == 0:
        return 1
        
    total = (1+n+1)*(n+1) // 2
    
    sums = sum(A)
    
    return total - sums
```