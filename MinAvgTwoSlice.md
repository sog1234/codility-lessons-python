[Question](https://app.codility.com/programmers/lessons/5-prefix_sums/min_avg_two_slice/)

```python
def solution(A):
    n = len(A)
    prefix = [0] * (n + 1)
    for i in range(n):
        prefix[i + 1] = prefix[i] + A[i]

    min_avg = prefix[2] / 2
    min_index = 0
    for i in range(n - 1):
        for j in range(i + 1, min(i+3, n)):
            avg = (prefix[j + 1] - prefix[i]) / (j - i + 1)
            if avg < min_avg:
                min_avg = avg
                min_index = i

    return min_index
```