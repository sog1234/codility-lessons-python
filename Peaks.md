[Question](https://app.codility.com/programmers/lessons/10-prime_and_composite_numbers/peaks/)

```python
def solution(A):
    n = len(A)

    if n < 3:
        return 0

    # prefix_peals[i+1] stores the number of peaks
    # from A[0] to A[i] where i > 0
    prefix_peaks = [0] * (n+1)
    # given indices i < j, need to know
    # the number of peaks from A[i] to A[j]
    # which is equal to prefix_peaks[j+1] - prefix_peaks[i]
    for i in range(1, n - 1):
        if A[i - 1] < A[i] > A[i + 1]:
            prefix_peaks[i+1] = prefix_peaks[i] + 1
        else:
            prefix_peaks[i+1] = prefix_peaks[i]
    prefix_peaks[n] = prefix_peaks[n-1]

    if prefix_peaks[n] == 0:
        return 0

    # note that the number of blocks
    # cannot exceed  the number of peaks
    for blocks in range(prefix_peaks[n], 1, -1):
        if n % blocks != 0:
            continue
        # size of each block
        size = n // blocks
        # start and end indices for block j
        j = 0
        start = 0
        end = size-1
        while j < blocks and prefix_peaks[end+1] - prefix_peaks[start] > 0:
            j += 1
            start += size
            end += size

        if j == blocks:
            return blocks

    return 1
```