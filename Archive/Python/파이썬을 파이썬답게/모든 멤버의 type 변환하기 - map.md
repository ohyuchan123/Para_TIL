# **모든 멤버의 type 변환하기 - map**
Iterable의 모든 멤버의 type을 변환하는 방법을 정리하였습니다.

예시)
- 문자열 배열 ['1', '100', '33']을 정수 배열 [1, 100, 33]로 바꾸기
- 부동소숫점 튜플 (3.14, 3.5, 22.6)을 정수 배열 (3, 3, 22)로 바꾸기

---

```python
list1 = ['1', '100', '33']
list2 = []
for value in list1:
    list2.append(int(value))
```

Python의 `map`을 사용하면 for문을 사용하지 않고도 멤버의 타입을 일괄 변환할 수 있습니다.

```python
list1 = ['1', '100', '33']
list2 = list(map(int, list1))
```