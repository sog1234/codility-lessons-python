[Question](https://app.codility.com/programmers/lessons/7-stacks_and_queues/fish/)

```python
def solution(A, B):
    n = len(A)
    
    # use stream[0] and stream[1], as upstream and downstream, 
    # to store the sizes of current living fish
    stream = [[], []]
    
    
    # go through the array, since every fish is downstream
    # of the previous one, before adding to the stack,
    # the eating can happen only if the downsteam is not empty
    # and the current fish is going upstream
    
    for i in range(n):
        if stream[1] and B[i] == 0:
            while stream[1] and stream[1][-1] < A[i]:
                dummy = stream[1].pop()
            if not stream[1]:
                stream[0].append(A[i])
            
        else:
            stream[B[i]].append(A[i])
            
    return len(stream[0]) + len(stream[1])
```