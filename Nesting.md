[Question](https://app.codility.com/programmers/lessons/7-stacks_and_queues/nesting/)
Determine whether a given string of parentheses (single type) is properly nested.
```python
def solution(S):
    n = len(S)
    
    if n == 0:
        return 1
        
    # to check if the string is properly nested
    # only need to check if it satisfies LIFO
    
    # use left as stack to store unpaired '('
    left = []
    
    for i in range(n):
        if S[i] == '(':
            left.append(S[i])
        else:
            if not left:
                return 0
            else:
                dummy = left.pop()
    
    if left:
        return 0
    else:
        return 1
```