---
title: "[Programmers_02] 전화번호 목록"
categories:
  - Dailycoding
tags:
  - algorithms
  - hash
---

# 문제
전화번호부에 적힌 전화번호 중, 한 번호가 다른 번호의 접두어인 경우가 있는지 확인하려 합니다.
전화번호가 다음과 같을 경우, 구조대 전화번호는 영석이의 전화번호의 접두사입니다.

구조대 : 119
박준영 : 97 674 223
지영석 : 11 9552 4421
전화번호부에 적힌 전화번호를 담은 배열 phone_book 이 solution 함수의 매개변수로 주어질 때, 어떤 번호가 다른 번호의 접두어인 경우가 있으면 false를 그렇지 않으면 true를 return 하도록 solution 함수를 작성해주세요.


[문제 링크](https://programmers.co.kr/learn/courses/30/lessons/42577)

### 입출력 예제
> phone_book	return  
[119, 97674223, 1195524421]	false  
[123,456,789]	true  
[12,123,1235,567,88]	false  


### 테스트 케이스
```
테스트 1
입력값 〉	["119", "97674223", "1195524421"]
기댓값 〉	false

테스트 2
입력값 〉	["123", "456", "789"]
기댓값 〉	true

테스트 3
입력값 〉	["12", "123", "1235", "567", "88"]
기댓값 〉	false
```

### 작성 코드 1
```
def solution(phone_book):
    phone_book.sort()

    for index in range(0,len(phone_book)-1):
        if phone_book[index] in phone_book[index+1]:
            return False
    return True
```

python 문자열이 들어있는 list를 정렬하면 숫자의 크기대로 정렬해줌
문자열 리스트도 문자열 길이로 정렬할 수 있 [m.sort(key=len)]

### 더 나은 코드 1
```
import collections

def solution(participant, completion):
    answer = collections.Counter(participant) - collections.Counter(completion)
    return list(answer.keys())[0]
```


### 더 나은 코드 2
```
def solution(participant, completion):
    participant.sort()
    completion.sort()
    for i in range(len(completion)):
        if participant[i] != completion[i]:
            return participant[i]
    return participant[len(participant)-1]
```
