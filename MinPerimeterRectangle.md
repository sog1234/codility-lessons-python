[Question](https://app.codility.com/programmers/lessons/10-prime_and_composite_numbers/min_perimeter_rectangle/)
Find the minimal perimeter of any rectangle whose area equals N.
```python
def solution(N):
    
    min_peri = 2 * (1 + N)
    i = 1
    
    while i*i <= N:
        if N % i == 0:
            peri = 2 * (i + N // i)
            if min_peri > peri:
                min_peri = peri
        i += 1
    
    return min_peri
```