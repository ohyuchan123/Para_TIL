# **이진 탐색하기 - binary search**

알고리즘 문제를 풀다 보면 이진 탐색을 써야할 때가 많습니다.  
이런 문제를 풀 때마다 이진 탐색 알고리즘을 작성하는 건 비효율적입니다.  
이번 시간엔 Python의 이진 탐색 모듈, bisect를 정리하였습니다.  

직접 반복문을 만들어, 이진 탐색 알고리즘을 구현합니다.
```python
def bisect(a, x, lo=0, hi=None):
    if lo < 0:
        raise ValueError('lo must be non-negative')
    if hi is None:
        hi = len(a)
    while lo < hi:
        mid = (lo + hi) // 2
        if a[mid] < x:
            lo = mid + 1
        else:
            hi = mid
    return lo

mylist = [1, 2, 3, 7, 9, 11, 33]
print(bisect(mylist, 3))

```