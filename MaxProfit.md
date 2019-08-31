[Question](https://app.codility.com/programmers/lessons/9-maximum_slice_problem/max_profit/)

```python
def solution(A):
    n = len(A)
    
    if n < 2:
        return 0
        
    # let p[i] be the max profit of selling on day i
    # then p[i+1] = max(0, p[i] + A[i+1] - A[i])
    
    max_profit = temp_profit = 0
    for i in range(1, n):
        # use temp_profit to store the max profit of
        # selling on day i
        temp_profit = max(0, temp_profit + A[i] - A[i-1])
        max_profit = max(max_profit, temp_profit)
    
    if max_profit < 0:
        return 0
    else:
        return max_profit
```