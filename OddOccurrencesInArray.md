[Question](https://app.codility.com/programmers/lessons/2-arrays/odd_occurrences_in_array/)

```python
def solution(A):
    A_dict = {} 
    
    for i in range(len(A)):
        A_dict[A[i]] = 0

    for i in range(len(A)):
        A_dict[A[i]] += 1

    for i in A_dict:
        if A_dict[i]%2 == 1:

    return i
```