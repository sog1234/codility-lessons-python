[Question](https://app.codility.com/programmers/lessons/17-dynamic_programming/number_solitaire/)

```python
def solution(A):
    n = len(A)
        
    # s[i] is the max sum for A[0] to A[i]
    s = [A[0]] * (max(n, 7))
    # initial values
    for i in range(1, min(n, 7)):
        s[i] += A[i]
        for j in range(1, i):
            if A[j] > 0:
                s[i] += A[j]
    # optimality relation:
    # s[i] = max_{0<k<7} (s[i-k]) + A[i]
    for i in range(7, n):
        s[i] = s[i-1]
        for k in range(2, 7):
            s[i] = max(s[i], s[i-k])
        s[i] += A[i]
            
    return s[n-1]
```