# **가장 많이 등장하는 알파벳 찾기 - Counter**

알고리즘 문제를 풀다 보면 어떤 원소 `x`가 주어진 시퀸스타입에 몇 번 등장하는지 세야 할 때가 있습니다.

---
보통은 반복문을 이용해 수를 셉니다.

```python
my_list = [1, 2, 3, 4, 5, 6, 7, 8, 7, 9, 1, 2, 3, 3, 5, 2, 6, 8, 9, 0, 1, 1, 4, 7, 0]
answer = {}
for number in my_list:
    try:
        answer[number] += 1
    except KeyError:
        answer[number] = 1

print(answer[1]) # = 4
print(answer[3])  # = 3
print(answer[100])  # =  raise KeyError
```

하지만 python에서는 collections.Counter 클래스를 사용하면 이 코드를 간략하게 만들 수 있습니다.

```python
from collections import Counter
my_list = [1, 2, 3, 4, 5, 6, 7, 8, 7, 9, 1, 2, 3, 3, 5, 2, 6, 8, 9, 0, 1, 1, 4, 7, 0]
answer = Counter(my_list)

print(answer[1]) # = 4
print(answer[3])  # = 3
print(answer[100]) # = 0
```