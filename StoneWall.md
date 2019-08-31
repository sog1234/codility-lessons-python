[Question](https://app.codility.com/programmers/lessons/7-stacks_and_queues/stone_wall/)

```python
def solution(H):
    n = len(H)
    
    stack = []
    count = 0
    
    for i in range(n):
        # if stack is empty
        # or H[i] is larger than the last element
        if not stack or stack[-1] < H[i]:
            stack.append(H[i])
        else:
            # then stack is not empty
            # and H[i] <= the last element
            while stack and H[i] < stack[-1]:
                # stack is not empty and H[i] < stack[-1]
                dummy = stack.pop()    
                count += 1
            # then stack is empty or stack[-1] <= H[i]
            if not stack or stack[-1] < H[i]:
                stack.append(H[i])
        
    
    return count + len(stack)
```