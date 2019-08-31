[Question](https://app.codility.com/programmers/lessons/4-counting_elements/missing_integer/)

```python
def solution(A):
    n_set = {i for i in range(1, len(A)+1)}
    for i in range(len(A)):
        n_set.discard(A[i])
        
    if not n_set:
        return len(A) + 1
    else:
        return min(n_set)
```