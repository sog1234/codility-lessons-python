[Question](https://app.codility.com/programmers/lessons/5-prefix_sums/passing_cars/)

```python
def solution(A):
    zero = []
    one = []
    pairs = 0
    
    for i in range(len(A)):
        if A[i] == 0:
            zero.append(i)
        else:
            one.append(i)
            
    if not zero or not one:
        return 0
        
    index = 0
    for i in range(len(zero)):
        # find the first 1
        while index < len(one) and one[index] <= zero[i]:
            index += 1
        
        # either index == len(one)
        if index == len(one):
            return pairs
            
        # or one[index] > zero[i]
        pairs += (len(one) - index)
        
        if pairs > 1000000000:
            return -1
        
    return pairs
```