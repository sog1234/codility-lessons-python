[Question](https://app.codility.com/programmers/lessons/5-prefix_sums/genomic_range_query/)
Find the minimal nucleotide from a range of sequence DNA.
```python
def solution(S, P, Q):
    n = len(S)
    str2factor = {'A': 1, 'C': 2, 'G': 3, 'T': 4}
    prefix = [[0]*(n+1), [0]*(n+1), [0]*(n+1), [0]*(n+1)]
    
    for i in range(n):
        factor = str2factor[S[i]]
        prefix[factor-1][i+1] = 1
        
    for i in range(1, n+1):
        for j in range(4):
            prefix[j][i] += prefix[j][i-1]
        
    m = len(P)
    factors = [0] * m
    
    for i in range(m):
        for j in range(4):
            occ = prefix[j][Q[i]+1] - prefix[j][P[i]]
            if occ > 0:
                factors[i] = (j+1)
                break
    
    return factors
```