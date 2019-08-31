[Question](https://app.codility.com/programmers/lessons/12-euclidean_algorithm/common_prime_divisors/)

```python
def gcd(a, b, res):
    if a == b:
        return a * res
    elif (a % 2 == 0) and (b % 2 == 0):
        return gcd(a // 2, b // 2, 2 * res)
    elif a % 2 == 0:
        return gcd(a // 2, b, res)
    elif b % 2 == 0:
        return gcd(a, b // 2, res)
    elif a > b:
        return gcd(a - b, b, res)
    else:
        return gcd(a, b - a, res)


# return 1 if a's prime divisor is also b's
def subset_primes(a, b):
    g = gcd(a, b, 1)
    
    if g == a:
        return 1
    elif g == 1:
        return 0
        
    return subset_primes(a // g, g)


# helper function
# return 1 if a and b have same set of prime divisors
def same_primes(a, b):
    # note that if a and b have the same set of prime divisors
    # gcd also has the same set of primes divisors
    g = gcd(a, b, 1)
    
    if g == 1 and a == b:
        return 1
    elif g == 1:
        return 0
    
    if subset_primes(a // g, g) and subset_primes(b // g, g):
        return 1
    else:
        return 0
        
        
def solution(A, B):
    n = len(A)
    count = 0
    
    for i in range(n):
        count += same_primes(A[i], B[i])
        
    return count
```