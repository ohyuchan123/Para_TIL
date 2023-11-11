이번에는 문자열 관련 함수들에 대해서 정리해볼까 한다. 이번 문자열 관련 함수들은 내가 현재까지도 애용하는 함수들이 있어서 GitHub TIL에 작성하게 되었다.

코테하면서 자주 사용했던 split은 정말 반가웠다. 너 덕분에 코딩테스트 참 유용했다.

## 문자열 관련 함수들

---

문자열 자료형은 자체적으로 함수를 가지고 있다.  
이들 함수를 다른 말로 ‘문자열 내장 함수’라고 한다. 이 내장 함수를 사용하려면 문자열 변수 이름 뒤에 ‘.’를 붙인 후 함수 이름을 써 주면 되다.  
이제 문자열의 내장 함수에 대해서 알아보자.

### 문자열 개수 세기 -count

---

```python
a = "hobby"
a.count('b')
2
```

count 함수로 문자열 중 문자 b의 개수를 리턴했다.

### 위치 알려 주기 1 - find

---

```python
a = "Python is the best choice"
a.find('b')
14
a.find('k')
-1
```

find 함수로 문자열 중 문자 b가 처음으로 나온 위치를 반환했다.  
만약 찾는 문자나 문자열이 존재하지 않는다면 -1을 반환한다.

> 파이썬은 숫자를 0부터 세기 때문에 b의 위치는 15가 아닌 14가 된다.

### 위치 알려 주기 2 - index

---

```python
a = "Life is too short"
a.index('t')
8
a.index('k')
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
ValueError: substring not found
```

index 함수로 문자열 중 문자 t가 맨 처음으로 나온 위치를 반환했다.  
만약 찾는 문자나 문자열이 존재하지 않는 다면 오류가 발생한다.  
앞의 find 함수와 다른 점은 문자열 안에 존재하지 않는 문자를 찾으면 오류가 발생한다는 것이다.

### 문자열 삽입 - join

---

```python
",".join('abcd')
'a,b,c,d'
```

join 함수로 abcd 문자열의 각각의 문자 사이에 ‘,’를 삽입했다.

join 함수는 문자열뿐만 아니라 앞으로 배울 리스트나 튜플도 입력으로 사용할 수 있다.

```python
",".join(['a', 'b', 'c', 'd'])
'a,b,c,d'
```

### 소문자를 대문자로 바꾸기 - upper

---

```python
a = "hi"
a.upper()
'HI'
```

upper 함수는 소문자를 대문자로 바꾸어 준다. 만약 문자열이 이미 대문자라면 아무런 변화도 일어나지 않을 것이다.

### 대문자를 소문자로 바꾸기 - lower

---

```python
**a = "HI"
a.lower()
'hi'**
```

lower 함수는 대문자를 소문자로 바꾸어 준다.

### 왼쪽 공백 지우기 - lstrip

---

```python
a = " hi "
a.lstrip()
'hi '
```

lstrip 함수는 문자열 중 가장 왼쪽에 있는 한 칸 이상의 연속된 공백들을 모두 지운다.

lstrip에서 l은 left를 의미한다.

### 오른쪽 공백 지우기 - rstrip

---

```python
a= " hi "
a.rstrip()
' hi'
```

rstrip 함수는 문자열 중 가장 오른쪽에 있는 한 칸 이상의 연속된 공백을 모두 지운다.

rstrip에서 r은 right를 의미한다.

### 양쪽 공백 지우기 - strip

---

```python
a = " hi "
a.strip()
'hi'
```

strip 함수는 문자열 양쪽에 있는 한 칸 이상의 연속된 공백을 모두 지운다.

### 문자열 바꾸기 - replace

---

```python
a = "Life is too short"
a.replace("Life", "Your leg")
'Your leg is too short'
```

replace 함수는 replace(바뀔*문자열, 바꿀*문자열)처럼 사용해서 문자열 안의 특정 한 값을 다른 값으로 치환해 준다.

### 문자열 나누기 - split

---

```python
a = "Life is too short"
a.split()
['Life', 'is', 'too', 'short']
b = "a:b:c:d"
b.split(':')
['a', 'b', 'c', 'd']
```

split 함수는 a.split()처럼 괄호 안에 아무 값도 넣어 주지 않으면  
공백(`[Space]`], `[Tab]`, `[Enter]`)을 기준으로 문자열을 나누어 준다.  
만약 b.split(':')처럼 괄호 안에 특정 값이 있을 경우에는 괄호 안의 값을 구분자로 해서 문자열을 나누어 준다.  
이렇게 나눈 값은 리스트에 하나씩 들어간다. `['Life', 'is', 'too', 'short']`나 `['a', 'b', 'c', 'd']`가 리스트인데,  
02-3에서 자세히 알아볼 것이므로 여기에서는 너무 신경 쓰지 않아도 된다.
