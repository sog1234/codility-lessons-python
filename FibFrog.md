[Question](https://app.codility.com/programmers/lessons/13-fibonacci_numbers/fib_frog/)

```python
def solution(A):
    n = len(A)

    if n < 3:
        return 1

    # indices of leaves
    leaves = [-1]
    for i in range(n):
        if A[i] == 1:
            leaves.append(i)
    # river bank as last leaf
    leaves.append(n)
    m = len(leaves)

    leaf2idx = {}
    for i in range(m):
        leaf2idx[leaves[i]] = i

    # find all fibonacci that are <= n+1
    fib = [1, 2, 3]
    f = fib[-1] + fib[-2]
    while f <= n + 1:
        fib.append(f)
        f = fib[-1] + fib[-2]
    k = len(fib)
    
    # now it is 0-1 Knapsack Problem
    # let jumps[i] be the min number of jumps from -1 to leaves[i]
    # jump[i] = m means that it is impossible to jump to leaves[i]
    jumps = [m] * m
    jumps[0] = 0

    for i in range(1, m):
        for j in range(0, k):
            diff = leaves[i] - fib[j]
            if diff < -1:
                continue
            elif diff == -1 or A[diff] == 1:
                idx = leaf2idx[diff]
                jumps[i] = min(jumps[i], jumps[idx]+1)

    if jumps[m-1] == m:
        return -1
    else:
        return jumps[m-1]
```