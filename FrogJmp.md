[Question](https://app.codility.com/programmers/lessons/3-time_complexity/frog_jmp/)

```python
def solution(X, Y, D):
    jump1 = (Y - X) // D
    jump2 = (Y - X) / D
    if jump1 == jump2:
        return jump1
    else:
        return jump1+1
```