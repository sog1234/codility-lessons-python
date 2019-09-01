[Question](https://app.codility.com/programmers/lessons/15-caterpillar_method/min_abs_sum_of_two/)

```python
def solution(A):
    n = len(A)
    
    A.sort()
    
    # all positive
    if A[0] >= 0:
        return A[0]*2
    # all negative
    if A[-1] <= 0:
        return -A[-1]*2
        
    # now A has both positive and negative
    # min (short for min abs sum of 2) must come from
    # one positive and one negative
    
    # find index of last negative and first positive
    neg = pos = -1
    for i in range(n-1):
        if A[i] < 0 and A[i+1] >= 0:
            neg = i
            break
        
    for i in range(n-1, 0, -1):
        if A[i] > 0 and A[i-1] <= 0:
            pos = i
            break
    
    # A[0] to A[neg] are negative
    # A[pos] to A[n-1] are positive
    
    # if A has 0    
    if pos-neg > 1:
        return 0
    
    min_abs2 = abs(A[neg]+A[pos])
    
    # front: index for positive
    front = n-1
    # back: index for negative
    # note min occurs possibly when A[back]+A[front] changes signs
    for back in range(pos):
        # find min for each back
        while front > neg and A[back] + A[front] >= 0:
            # front moves backwards
            front -= 1
    
        # either front == neg, then A[back]+A[front+1] >= 0
        if front == neg:
            return min(A[back] + A[front+1], min_abs2)
        # or front > neg, then A[back]+A[front]<0, 
        # if front == n-1, then min for back
        # is -(A[back]+A[front])
        elif front == n-1:
            min_abs2 = min(-(A[back]+A[front]), min_abs2)
        # if front < n-1, then A[back]+A[front+1]>=0
        # now the min for back is between
        # A[back]+A[front+1] and -(A[back]+A[front])
        else:
            min_abs2 = min(A[back]+A[front+1], -(A[back]+A[front]), min_abs2)
            
    return min_abs2
```