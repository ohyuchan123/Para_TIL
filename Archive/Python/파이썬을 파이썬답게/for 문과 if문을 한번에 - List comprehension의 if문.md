# **for 문과 if문을 한번에 - LIst comprehension이 if문**
list comprehension 안에서 조건문을 넣는 방법에 대해 정리하였습니다.

보통은 for문 안에서 조건문을 사용해 2-depth 블록을 만듭니다.

```python
mylist = [3,2,6,7]
answer = []
for number in mylist:
    if number%2==0:
        answer.append(number**2)
```

python에서는 list comprehension을 사용하면 한 줄 안에 for문과 if문을 한 번에 처리할 수 있습니다.
```python
mylist = [3,2,6,7]
answer = [number**2 for number in mylist if number%2==0]
```
list comprehension의 syntax는 Displays for lists, sets and dictionaries 에서 확인할 수 있습니다.