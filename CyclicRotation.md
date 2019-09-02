[Question](https://app.codility.com/programmers/lessons/2-arrays/cyclic_rotation/)
Rotate an array to the right by a given number of steps.
```python
def solution(A, K): 
    if len(A) == 0:
        return A
        
    K = K % len(A)
    
    if K == 0: 
        return A
        
    B = [0]*len(A)
    
    for i in range(len(A)): 
        index = (i+K) % len(A)
        B[index] = A[i]
        
    return B
```