# **i번째 원소와 i+1번째 원소 - zip**

보통은 다음과 같이 len과 index를 이용하여 각 원소에 접근합니다.

```python
def solution(mylist):
    answer = []
    for i in range(len(mylist)-1):
        answer.append(abs(mylist[i] - mylist[i+1]))
    return answer

if __name__ == '__main__':
    mylist = [83, 48, 13, 4, 71, 11]    
    print(solution(mylist))
```

python에서는

python의 zip을 이용하여 index를 사용하지 않고 각 원소에 접근할 수 있습니다.

```python
def solution(mylist):
    answer = []
    for number1, number2 in zip(mylist, mylist[1:]):
        answer.append(abs(number1 - number2))
    return answer

if __name__ == '__main__':
    mylist = [83, 48, 13, 4, 71, 11]    
    print(solution(mylist))
```

※ 주의  

zip 함수에 서로 길이가 다른 리스트가 인자로 들어오는 경우에는 길이가 짧은 쪽 까지만 이터레이션이 이루어집니다. 더 자세한 내용은 공식 레퍼런스 - zip의 내용을 참고해주세요.