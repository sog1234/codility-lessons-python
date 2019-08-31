[Question](https://app.codility.com/programmers/lessons/6-sorting/number_of_disc_intersections/)

```python
def solution(A):
    n = len(A)

    if n < 2:
        return 0

    lr = [(i - A[i], i + A[i]) for i in range(n) if A[i] < 99999]

    m = len(lr)

    if m < 2:
        return (n - m) * (n - m - 1) // 2 + m * (n - m)

    lr.sort(key=lambda x: x[0])
    # note that j and k (j < k) intersect if left point of k
    # is less then or equal to right point of j

    count = 0

    for i in range(m-1):
        # now compare the right point of lr[i] with
        # the left points of the lr[i+1] ... lr[m-1]
        # since the left points are sorted, can use binary search
        # use binary search to find the largest left end point that
        # is less than or equal to the right point of lr[i]

        # i does not intersects with hi, ...
        hi = m
        # i intersects with i, ..., lo
        lo = i
        j = m-1
        while (hi - lo) > 1:
            if lr[j][0] <= lr[i][1]:
                # i intersects with i, ..., j
                lo = j
            else:
                # i does not intersect with j, j+1, ...
                hi = j
            j = (lo + hi) // 2

        # hi = lo + 1
        # i intersects i, ..., lo
        count += (lo - i)
        if count > 10000000:
            return -1
    return count + (n - m) * (n - m - 1) // 2 + m * (n - m)
```