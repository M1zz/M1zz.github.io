---
title: "[Programmers_09] 기능개발"
categories:
  - Dailycoding
tags:
  - algorithms
  - queue
---

# 문제
문제 설명
프로그래머스 팀에서는 기능 개선 작업을 수행 중입니다. 각 기능은 진도가 100%일 때 서비스에 반영할 수 있습니다.

또, 각 기능의 개발속도는 모두 다르기 때문에 뒤에 있는 기능이 앞에 있는 기능보다 먼저 개발될 수 있고, 이때 뒤에 있는 기능은 앞에 있는 기능이 배포될 때 함께 배포됩니다.

먼저 배포되어야 하는 순서대로 작업의 진도가 적힌 정수 배열 progresses와 각 작업의 개발 속도가 적힌 정수 배열 speeds가 주어질 때 각 배포마다 몇 개의 기능이 배포되는지를 return 하도록 solution 함수를 완성하세요.

[문제 링크](https://programmers.co.kr/learn/courses/30/lessons/42586)

### 입출력 예제
> progresses	speeds	return  
[93,30,55]	[1,30,5]	[2,1]  

### 테스트 케이스
```
테스트 1
입력값 〉	[93, 30, 55], [1, 30, 5]
기댓값 〉	[2, 1]
```

### 작성 코드 1
```
def solution(heights):
    heights_list = [p for p in enumerate(heights)]
    heights_temp = []

    for item_num in range(1,len(heights)):
        for part in reversed(heights_list[:item_num]):
            if heights_list[item_num][1] < part[1]:
                heights_temp.append(part[0]+1)
                break
        if len(heights_temp) != len(heights_list[:item_num]):
            heights_temp.append(0)
    heights_temp.insert(0,0)
    return heights_temp
```

### 더 나은 코드 1
```
def solution(heights):
    ans = [0] * len(h)
    for i in range(len(h)-1, 0, -1):
        for j in range(i-1, -1, -1):
            if h[i] < h[j]:
                ans[i] = j+1
                break
    return ans
```
