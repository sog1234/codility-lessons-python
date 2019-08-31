[Question](https://app.codility.com/programmers/lessons/4-counting_elements/max_counters/)

```python
def solution(N, A):
    counters = [0] * N
    max_val = 0
    sums = 0
    
    for i in range(len(A)):
        if A[i] <= N:
            counters[A[i]-1] += 1
            sums += 1
            if max_val < counters[A[i]-1]:
                max_val = counters[A[i]-1]
        elif sums < max_val * N:
            counters = [max_val] * N
            
    return counters
```