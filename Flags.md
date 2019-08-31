[Question](https://app.codility.com/programmers/lessons/10-prime_and_composite_numbers/flags/)

```python
from math import sqrt, floor


def solution(A):
    n = len(A)

    if n < 3:
        return 0

    # peaks is a list of indices of peaks
    peaks = []
    for i in range(1, n - 1):
        if A[i - 1] < A[i] > A[i + 1]:
            peaks.append(i)

    m = len(peaks)
    if m < 3:
        return m

    # note max number of flags cannot
    # exceed sqrt(peaks[m-1]-peaks[0])
    max_flags = min(m, floor(sqrt(peaks[m-1]-peaks[0]))+1)
    for flags in range(max_flags, 2, -1):
        count = 1
        # index of current flag
        i = 0
        # index of next flag
        j = 1
        while j < m:
            if flags <= (peaks[j] - peaks[i]):
                count += 1
                if flags-count > m-1-j:
                    break
                if count == flags:
                    return flags
                i = j
                j += 1
            else:
                j += 1

    return 2
```