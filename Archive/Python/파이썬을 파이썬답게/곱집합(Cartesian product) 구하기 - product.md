# **곱집합(Cartesian product) 구하기 - product**
iterable으로 곱집합을 구하는 방법에 대해서 정리하였습니다.

예시 ) 두 스트링 'ABCD','xy'의 곱집합은 Ax Ay Bs By Cx Cy Dx Dy입니다.

---

보통은 for문을 이용해 두 iterable의 원소를 하나씩 곱해값니다.
```python
iterable1 = 'ABCD'
iterable2 = 'xy'
iterable3 = '1234'

for value1 in iterable1:
    for value2 in iterable2:
        for value3 in iterable3:
            print(value1, value2, value3)
```

Python에서는

itertools.product를 이용하면, for문을 사용하지 않고도 곱집합을 구현할 수 있다.

```python
import itertools

iterable1 = 'ABCD'
iterable2 = 'xy'
iterable3 = '1234'
print(list(itertools.product(iterable1, iterable2, iterable3)))
```