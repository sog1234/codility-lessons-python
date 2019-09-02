[Question](https://app.codility.com/programmers/lessons/15-caterpillar_method/abs_distinct/)
Compute number of distinct absolute values of sorted array elements.
```python
# assume A[start] to A[end] have the same sign including zeros
# then count number of distinct values
def same_sign(A, start, end):
    count = end - start + 1

    front = start +1
    for back in range(start, end + 1):
        if front == back:
            front += 1
        while front < end + 1 and A[front] == A[back]:
            count -= 1
            front += 1

    return count


# count the number of pairs opposite numbers
# [-1, -1, 1, 1, 1] counted as 1
def opposite_sign(A, first, last):
    n = len(A)

    if last - first > 1:
        pairs = -1
    else:
        pairs = 0

    # A[0] to A[first-1] are negative
    # A[last+1] to A[n-1] are positive
    forward = last

    for backward in range(first, -1, -1):
        count = 0
        while forward < n and A[forward] + A[backward] <= 0:
            if A[forward] + A[backward] == 0:
                count += 1
            forward += 1
        # ignore repetition
        if count > 0:
            pairs += 1

    return pairs


def solution(A):
    n = len(A)

    # first is the index of largest negative
    # last is the index of smallest positive
    first, last = -1, n
    for i in range(n):
        if A[i] >= 0:
            first = i- 1
            break
    for i in range(n - 1, -1, -1):
        if A[i] <= 0:
            last = i + 1
            break

    # if A does not have both positive and negative
    if first == -1 or last == n:
        return same_sign(A, 0, n - 1)
    else:
        return same_sign(A, last, n - 1) + same_sign(A, 0, first) - opposite_sign(A, first, last)
```