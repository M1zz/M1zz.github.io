---
title: "[Programmers_03] 체육복"
categories:
  - Dailycoding
tags:
  - algorithms
  - greedy
---

# 문제
문제 설명
점심시간에 도둑이 들어, 일부 학생이 체육복을 도난당했습니다. 다행히 여벌 체육복이 있는 학생이 이들에게 체육복을 빌려주려 합니다. 학생들의 번호는 체격 순으로 매겨져 있어, 바로 앞번호의 학생이나 바로 뒷번호의 학생에게만 체육복을 빌려줄 수 있습니다. 예를 들어, 4번 학생은 3번 학생이나 5번 학생에게만 체육복을 빌려줄 수 있습니다. 체육복이 없으면 수업을 들을 수 없기 때문에 체육복을 적절히 빌려 최대한 많은 학생이 체육수업을 들어야 합니다.

전체 학생의 수 n, 체육복을 도난당한 학생들의 번호가 담긴 배열 lost, 여벌의 체육복을 가져온 학생들의 번호가 담긴 배열 reserve가 매개변수로 주어질 때, 체육수업을 들을 수 있는 학생의 최댓값을 return 하도록 solution 함수를 작성해주세요.


[문제 링크](https://programmers.co.kr/learn/courses/30/lessons/42862)

### 입출력 예제
> n	lost	reserve	return
5	[2, 4]	[1, 3, 5]	5
5	[2, 4]	[3]	4
3	[3]	[1]	2


### 테스트 케이스
```
테스트 1
입력값 〉	5, [2, 4], [1, 3, 5]
기댓값 〉	5

테스트 2
입력값 〉	5, [2, 4], [3]
기댓값 〉	4
```

### 작성 코드 1
```
def solution(n, lost, reserve):
    reserve_set = set(reserve) - set(lost)
    lost_set = set(lost) - set(reserve)

    print(reserve_set,lost_set)

    for user in lost_set:
        if (user - 1) in reserve_set:
            lost_set.remove(user - 1)
        elif (user + 1) in reserve_set:
            lost_set.remove(user + 1)
    return n - len(lost_set)
```

### 작성 코드 2
```
def solution(n, lost, reserve):
    reserve_set = set(reserve) - set(lost)
    lost_set = set(lost) - set(reserve)

    print(reserve_set,lost_set)

    for user in reserve_set:
        if (user - 1) in lost_set:
            lost_set.remove(user - 1)
        elif (user + 1) in lost_set:
            lost_set.remove(user + 1)
    return n - len(lost_set)
```





### 더 나은 코드 1
```
def solution(n, lost, reserve):
    _reserve = [r for r in reserve if r not in lost]
    _lost = [l for l in lost if l not in reserve]
    for r in _reserve:
        f = r - 1
        b = r + 1
        if f in _lost:
            _lost.remove(f)
        elif b in _lost:
            _lost.remove(b)
    return n - len(_lost)
```
참고할 만한 코드가 없다
