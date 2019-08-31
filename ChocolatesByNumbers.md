[Question](https://app.codility.com/programmers/lessons/12-euclidean_algorithm/chocolates_by_numbers/)

```python
def gcd(a, b, res):
    if a == b:
        return a * res
    elif (a % 2 == 0) and (b % 2 == 0):
        return gcd(a // 2, b // 2, 2 * res)
    elif a % 2 == 0:
        return gcd(a //2, b, res)
    elif b % 2 == 0:
        return gcd(a, b // 2, res)
    elif a > b:
        return gcd(a - b, b, res)
    else:
        return gcd(a, b - a, res)
        

def solution(n, m):
    
    # need to find smallest positive k
    # such that km mod n == 0
    # thus, k = lcm(m, n) // m
    
    return n // gcd(m, n, 1)
```