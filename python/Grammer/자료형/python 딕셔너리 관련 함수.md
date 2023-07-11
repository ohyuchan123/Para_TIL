# 😎 딕셔너리 관련 함수

오늘은 딕셔너리를 자유자재로 사용하기 위해 딕셔너리가 자체적으로 가지고 있는 함수를 정리해 보려고 한다.

## 딕셔너리란?

---

딕셔너리는 단어 그대로 ‘사전’이라는 뜻이다. 즉 “people”이라는 단어에 “사람”,  
“baseball”이라는 단어에 “야구”라는 뜻이 부합되듯이 딕셔너리는 Key와 Value를 한 쌍으로 가지는 자료형이다.  
예컨대 Key가 “baseball”이라면 Value “야구”가 될 것이다.

![Alt text](/python/Grammer/img/image.png)

딕셔너리는 리스트나 튜플처럼 순차적으로(sequential) 해당 요솟값을 구하지 않고  
Key를 통해 Value를 얻는다. 이것이 바로 딕셔너리의 가장 큰 특징이다.  
baseball이라는 단어의 뜻을 찾기 위해 사전의 내용을 순차적으로 모두 검색하는 것이 아니라 baseball이라는 단어가 있는 곳만 펼쳐 보는 것이다.

## 딕셔너리 관련 함수

---

딕셔너리를 자유자재로 사용하기 위해 딕셔너리가 자체적으로 가지고 있는 함수를 사용해 보자

### Key 리스트 만들기 - keys

---

```python
a = {'name': 'pey', 'phone': '010-9999-1234', 'birth': '1118'}
a.keys()
dict_keys(['name', 'phone', 'birth'])
```

a.keys()는 딕셔너리 a의 Key만을 모아 dict_keys 객체를 리턴한다.

dict_keys 객체는 다음과 같이 사용할 수 있다. 리스트를 사용하는 것과 별 차이는 없지만,  
리스트 고유의 append, insert, pop, remove, sort 함수는 수행할 수 없다.

```python
for k in a.keys():
...    print(k)
...
name
phone
birth
```

- print(k)를 입력할 때 들여쓰기하지 않으면 오류가 발생하므로 주의하자.
- for 문 등 반복 구문에 대해서는 03장에서 자세히 살펴본다.

dict_keys 객체를 리스트로 변환하려면 다음과 같이 하면 된다.

```python
list(a.keys())
['name', 'phone', 'birth']
```

### Value 리스트 만들기 - values

---

```python
a.values()
dict_values(['pey', '010-9999-1234', '1118'])
```

Key를 얻는 것과 마찬가지 방법으로 Value만 얻고 싶다면 values 함수를 사용하면 된다. values 함수를 호출하면 dict_values 객체를 리턴한다.

### Key, Value 쌍 얻기 - items

---

```python
a.items()
dict_items([('name', 'pey'), ('phone', '010-9999-1234'), ('birth', '1118')])
```

items 함수는 Key와 Value의 쌍을 튜플로 묶은 값을 dict_items 객체로 리턴한다.

### Key : Value 쌍 모두 지우기 - clear

---

```python
a.clear()
a
{}
```

clear 함수는 딕셔너리 안의 모든 요소를 삭제한다.

> 빈 리스트를 [], 빈 튜퓰을 ()로 표현하는 것과 마찬가지로 빈 딕셔너리도 {}로 표현한다.

### Key로 Value 얻기 - get

---

```python
a = {'name': 'pey', 'phone': '010-9999-1234', 'birth': '1118'}
a.get('name')
'pey'
a.get('phone')
'010-9999-1234'
```

get(x) 함수는 x라는 Key에 대응되는 Value를 리턴한다. 앞에서 살펴보았듯이 `a.get('name')` 은 `a[’name’]` 을 사용했을 때와 동일한 결괏값을 리턴한다.

### 해당 Key가 딕셔너리 안에 있는지 조사하기 - in

---

```python
a = {'name':'pey', 'phone':'010-9999-1234', 'birth': '1118'}
'name' in a
True
'email' in a
False
```

'name' 문자열은 a 딕셔너리의 Key 중 하나이다. 따라서 'name' in a를 호출하면 참(True)을 리턴한다.  
이와 반대로 'email'은 a 딕셔너리 안에 존재하지 않는 Key이므로 거짓(False)을 리턴한다.
