[Question](https://app.codility.com/programmers/lessons/11-sieve_of_eratosthenes/count_semiprimes/)
Count the semiprime numbers in the given range [a..b]
```python
def solution(n, P, Q):
    m = len(P)

    if n < 4:
        return [0] * m

    # given i <= n, need to find number of semiprimes
    # between 1 and i.
    # how to determine if a number k is semiprime?
    # if k only has two prime factors

    # step 1:
    # create an array factor in which each factor[i] is the smallest
    # prime factor of i if i is composite
    factor = [0] * (n + 1)
    i = 2
    while i * i <= n:
        # if i is prime
        if factor[i] == 0:
            for k in range(i * i, n + 1, i):
                # k is composite
                # if k does not have prime factor less than i
                if factor[k] == 0:
                    # the smallest prime factor of k is i
                    factor[k] = i
        i += 1

    # step 2:
    # use array factor to check if i has only two prime factors
    # i.e., if factor[x//factor[x]] == 0
    # create an array prefix such that
    # prefix[i] is number of semiprimes between 1 to i
    # then number of semiprimes between i and j
    # is prefix[j]-prefix[i-1]

    prefix = [0] * (n + 1)
    for i in range(4, n + 1):
        # if i is composite with its smallest prime factor factor[i]
        if factor[i] != 0:
            # if i//factor[i] is prime
            if factor[i // factor[i]] == 0:
                prefix[i] = 1
        prefix[i] += prefix[i - 1]

    sol = [0] * m
    for i in range(m):
        sol[i] = prefix[Q[i]] - prefix[P[i] - 1]

    return sol
```