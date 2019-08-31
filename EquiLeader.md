[Question](https://app.codility.com/programmers/lessons/8-leader/equi_leader/)

```python
def solution(A):
    n = len(A)

    if n == 1:
        return 0

    # first note that the leader of two
    # sequences have to be the leader of
    # of the original sequence

    # find the leader of A
    size = 0
    for i in range(n):
        if size == 0:
            val = A[i]
            size += 1
        else:
            if val == A[i]:
                size += 1
            else:
                size -= 1

    if size == 0:
        return 0

    count = 0
    for i in range(n):
        if A[i] == val:
            count += 1

    if count > n // 2:
        leader = val
    else:
        return 0

    # store the number of occurrence of leader in A[0] ... A[i]
    left = [0] * n
    # store the number of occurrence of leader in A[i] ... A[n-1]
    right = [0] * n

    # initialization
    if A[0] == leader:
        left[0] = 1
    if A[n - 1] == leader:
        right[n - 1] = 1

    for i in range(1, n):
        if A[i] == leader:
            left[i] = left[i - 1] + 1
        else:
            left[i] = left[i - 1]
            
        if A[n - i - 1] == leader:
            right[n - i - 1] = right[n - i] + 1
        else:
            right[n - i - 1] = right[n - i]

    s = 0
    for i in range(n - 1):
        if left[i] / (i + 1) > 0.5 and right[i + 1] / (n - i - 1) > 0.5:
            s += 1

    return s
```