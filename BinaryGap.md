[Question](https://app.codility.com/programmers/lessons/1-iterations/binary_gap/)

```python
def solution(N):
    bi_str = bin(N) 
    bi_gap = 0 
    i = 0 
    
    while i < len(bi_str):
        if bi_str[i] == '1':
            count = 0
            i += 1
            // find the number of consecutive zeros
            while i < len(bi_str) and bi_str[i] == '0':
                count += 1 
                i += 1
                
            // now either i == len(bi_str) 
            if i == len(bi_str):
                return bi_gap 
            // or bi_str[i] == '1' 
            if count > bi_gap:
                bi_gap = count

            // decrement i 
            i -= 1

        i += 1

    return bi_gap
```