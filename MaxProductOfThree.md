[Question](https://app.codility.com/programmers/lessons/6-sorting/max_product_of_three/)
Maximize A[P] * A[Q] * A[R] for any triplet (P, Q, R).
```python
def solution(A):
    A.sort()
    n = len(A)
    pos = -1
    for i in range(n):
        if A[i] >= 0:
            pos = i
            break
    
    # if all elements are negative
    # or if there is at most one negative
    if pos == -1 or pos <= 1:
        return A[n-3]*A[n-2]*A[n-1]
    
    # then there are at least two negatives and one positive
    prod1 = A[0]*A[1]*A[n-1]
    prod2 = A[n-3]*A[n-2]*A[n-1]
    if prod1 > prod2:
        return prod1
    else:
        return prod2
```