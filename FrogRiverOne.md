[Question](https://app.codility.com/programmers/lessons/4-counting_elements/frog_river_one/)
Find the earliest time when a frog can jump to the other side of a river.
```python
def solution(X, A):
    A_set = set()

    for i in range(len(A)):
        A_set.add(A[i])
        if len(A_set) == X:
            return i
            
    return -1
```