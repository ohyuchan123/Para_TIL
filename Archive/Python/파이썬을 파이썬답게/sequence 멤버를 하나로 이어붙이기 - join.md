# **sequence 멤버를 하나로 이어붙이기 - join**
알고리즘 문제를 풀다보면, 시퀸스의 멤버들을 하나의 string으로 이어붙여야 할 때가 있습니다.

예시)
- 문자열 배열 ['1', '100', '33']을 이어 붙여 문자열 '110033' 만들기
- 정수형 튜플 (3, 22, 91)을 이어붙여 문자열 '32291' 만들기

---

다른 언어에서는 for문을 이용해 원소를 하나씩 이어 붙입니다.

```python
my_list = ['1', '100', '33']
answer = ''
for value in my_list:
    answer += value
```

하지만 Python에서는 str.joiniterable)을 사용하면 이 코드를 두 줄로 줄일 수 있습니다.

```python
my_list = ['1', '100', '33']
answer = ''.join(my_list)
```