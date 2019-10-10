---
title: "[Programmers_12] K번째수"
categories:
  - Dailycoding
tags:
  - algorithms
  - sorting
---

# 문제
배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하려 합니다.

예를 들어 array가 [1, 5, 2, 6, 3, 7, 4], i = 2, j = 5, k = 3이라면

array의 2번째부터 5번째까지 자르면 [5, 2, 6, 3]입니다.
1에서 나온 배열을 정렬하면 [2, 3, 5, 6]입니다.
2에서 나온 배열의 3번째 숫자는 5입니다.
배열 array, [i, j, k]를 원소로 가진 2차원 배열 commands가 매개변수로 주어질 때, commands의 모든 원소에 대해 앞서 설명한 연산을 적용했을 때 나온 결과를 배열에 담아 return 하도록 solution 함수를 작성해주세요.

[문제 링크](https://programmers.co.kr/learn/courses/30/lessons/42748)

### 입출력 예제
> array	commands	return  
[1, 5, 2, 6, 3, 7, 4]	[[2, 5, 3], [4, 4, 1], [1, 7, 3]]	[5, 6, 3]  

### 테스트 케이스
```
테스트 1
입력값 〉	[1, 5, 2, 6, 3, 7, 4], [[2, 5, 3], [4, 4, 1], [1, 7, 3]]
기댓값 〉	[5, 6, 3]
```

### 작성 코드 1
```
def solution(array, commands):
    answer = []
    for item in commands :
        temp = []
        temp = array[item[0]-1:item[1]]
        temp.sort()
        answer.append(temp[item[2]-1])
    return answer
```

### 더 나은 코드 1
```
def solution(array, commands):
    return list(map(lambda x:sorted(array[x[0]-1:x[1]])[x[2]-1], commands))
```

### 더 나은 코드 2
```
def solution(array, commands):
    answer = []
    for command in commands:
        i,j,k = command
        answer.append(list(sorted(array[i-1:j]))[k-1])
    return answer
```
