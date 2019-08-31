[Question](https://app.codility.com/programmers/lessons/13-fibonacci_numbers/ladder/)

```python
def solution(A, B):
    # let F(n) be the number of different
    # ways of climbing n rungs
    # then it can be achieved through two
    # ways: 1) first climb n-1 rungs and then
    # climb the nth rung, 2) first climb n-2
    # rungs and then climb last 2 rungs
    # thus, F(n) = F(n-1) + F(n-2)

    l = len(A)

    # F[i] is the number of ways of climbing i rungs
    # modulo 2^30
    F = [1] * (l + 1)
    F[1] = 1

    for i in range(2, l + 1):
        F[i] = (F[i - 1] + F[i - 2]) % (2 ** 30)

    return [F[A[i]] % (2 ** B[i]) for i in range(l)]
```