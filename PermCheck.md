[Question](https://app.codility.com/programmers/lessons/4-counting_elements/perm_check/)

```python
def solution(A):
    n = len(A)
    A_set = set(A)
    n_set = len(A_set)
    max_set = max(A_set)
    
    if n_set == n and max_set == n:
        return 1
    else:
        return 0
```