[Question](https://app.codility.com/programmers/lessons/5-prefix_sums/count_div/)

```python
def solution(A, B, K):
    # note that from A to A+K-1 only one of them is divisible by K
    n = (B - A + 1) // K
    m = (B - A + 1) % K

    if m == 0:
        return n

    # note that from B-m+1 to B, at most one is divisible by K
    r = (B - m + 1) % K
    
    if r == 0 or (r + m - 1) > K:
        return n + 1
    else:
        return n
```