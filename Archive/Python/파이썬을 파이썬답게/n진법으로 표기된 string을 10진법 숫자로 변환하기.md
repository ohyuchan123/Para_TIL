# **n진법으로 표기된 string을 10진법 숫자로 변환하기**

진법 변환 문제는 알고리즘 문제나 숙제로 자주 나오는 유형입니다. 이번에는 n진법으로 표기된 문자열을 10진법 숫자로 변환하는 방법을 작성합니다.

예시) 5진법으로 적힌 문자열 '3212'를 10진법으로 바꾸기

---

다른 언어에서는..  
```python
num = '3212'
base = 5

answer = 0
for idx, number in enumerate(num[::-1]):
    answer += int(number) * (base ** idx)
```

Python에서는

Python의 int(x,base=10) 함수는 진법 변환을 지원합니다.  
이 기본적인 함수를 잘 쓰면 코드를 짧게 쓸 수 있고, 또 시간을 절약할 수 있습니다.  
```python
num = '3212'
base = 5
answer = int(num, base)
```

**10진수 -> 2,8,16진수**
```
2진수 -> bin()
8진수 -> oct()
16진수-> hex()
```

**10진수 -> n진수**
```
convert(10,2)
```