[Question](https://app.codility.com/programmers/lessons/17-dynamic_programming/min_abs_sum/)
Given array of integers, find the lowest absolute sum of elements.
```python
def solution(A):
    # time complexity: O(n * max(A) ^ 2)
    # space complexity: O(sum(A))

    A = [abs(a) for a in A]
    total = sum(A)
    half = total // 2
    
    # Let P (N) be set of elements in A that are assigned '+' ('-').
    # Suppose sum(P) <= sum(N)
    # 2 * sum(P) <= sum(P) + sum(N) = sum(A)
    
    from collections import Counter
    count = Counter(A)
    
    # Let dp[i][j] be -1 if can not get j using count.keys()[0:i]
    # and max number of count[count.keys()[i]] left to get j using count.keys()[0:i]
    # Base case: dp[0][0] = 1
    # Optimality relation:
    # If dp[i-1][j] >= 0, it means can use count.keys()[0:i-1] to get j, thus, we do not need to use count[count.keys()[i]]
    # and the number of count[count.keys()[i]] left is count[count.keys()[i]]. Thus, dp[i][j] = count[count.keys()[i]].
    # If dp[i-1][j] = -1, it means cannot use count.keys()[0:i-1] to get j. 
    # If dp[i][j-a] > 0, it means can use count.keys()[0:i] to get (j - a) and there are dp[i][j-a] number of a left.
    # Thus, dp[i][j] = dp[i][j-a] - 1
    dp = [0] + [-1] * (half)

    for a, c in count.items():
        for j in range(half + 1):
            if dp[j] >= 0:
                dp[j] = c
            elif j >= a and dp[j-a] > 0:
                dp[j] = dp[j-a] - 1

    for j in range(half, -1, -1):
        if dp[j] >= 0:
            return total - 2 * j
    # only one element in A
    return A[0]
```
