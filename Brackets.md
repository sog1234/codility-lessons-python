[Question](https://app.codility.com/programmers/lessons/7-stacks_and_queues/brackets/)

```python
def solution(S):
    n = len(S)
    
    if n == 0:
        return 1
        
    
    # to check if the string is properly nested
    # only need to check if the string satisfies LIFO
    left = {'(', '[', '{'}
    
    br2val = {'(': 1, ')': 1, '[': 2, ']': 2, '{': 3, '}': 3}
    
    left_stack = []
    
    for i in range(n):
        if S[i] in left:
            left_stack.append(S[i])
        else:
            if len(left_stack) == 0:
                return 0
            s = left_stack.pop()
            if br2val[s] != br2val[S[i]]:
                return 0
    
    if len(left_stack) != 0:
        return 0
    else:
        return 1
```