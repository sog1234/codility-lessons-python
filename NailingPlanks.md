[Question](https://app.codility.com/programmers/lessons/14-binary_search_algorithm/nailing_planks/)
Count the minimum number of nails that allow a series of planks to be nailed.
```python
def check(A, B, C, st, mid):
    n = len(A)
    m = len(C)
    # given A[k] and B[k]
    # need to find if there is C[l] in between

    # use prefix[i] to count the number of C's
    # that are less than or equal to i

    # then the number of C's in [A[k], B[k]]
    # is prefix[B[k]] - prefix[A[k]-1]

    prefix = [0] * (2 * m + 1)

    for i in range(mid):
        prefix[C[i]] = 1

    for i in range(1, 2 * m + 1):
        prefix[i] += prefix[i - 1]

    for k in range(st, n):
        if prefix[B[k]] == prefix[A[k] - 1]:
            return 0, k
    return 1, 0


def solution(A, B, C):
    m = len(C)

    j = -1
    # note j is between 1 and m if exists
    lo = 1
    hi = m

    # start index for A and B
    st = 0
    while lo <= hi:
        mid = (lo + hi) // 2
        success, st = check(A, B, C, st, mid)
        if success:
            hi = mid - 1
            j = mid
        else:
            lo = mid + 1

    return j
```