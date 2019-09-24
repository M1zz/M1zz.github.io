---
title: "[Programmers_07] 탑"
categories:
  - Dailycoding
tags:
  - algorithms
  - queue
---

# 문제
수평 직선에 탑 N대를 세웠습니다. 모든 탑의 꼭대기에는 신호를 송/수신하는 장치를 설치했습니다. 발사한 신호는 신호를 보낸 탑보다 높은 탑에서만 수신합니다. 또한, 한 번 수신된 신호는 다른 탑으로 송신되지 않습니다.

예를 들어 높이가 6, 9, 5, 7, 4인 다섯 탑이 왼쪽으로 동시에 레이저 신호를 발사합니다. 그러면, 탑은 다음과 같이 신호를 주고받습니다. 높이가 4인 다섯 번째 탑에서 발사한 신호는 높이가 7인 네 번째 탑이 수신하고, 높이가 7인 네 번째 탑의 신호는 높이가 9인 두 번째 탑이, 높이가 5인 세 번째 탑의 신호도 높이가 9인 두 번째 탑이 수신합니다. 높이가 9인 두 번째 탑과 높이가 6인 첫 번째 탑이 보낸 레이저 신호는 어떤 탑에서도 수신할 수 없습니다.

송신 탑(높이)	수신 탑(높이)  
5(4)	4(7)  
4(7)	2(9)  
3(5)	2(9)  
2(9)	-  
1(6)	-  

맨 왼쪽부터 순서대로 탑의 높이를 담은 배열 heights가 매개변수로 주어질 때 각 탑이 쏜 신호를 어느 탑에서 받았는지 기록한 배열을 return 하도록 solution 함수를 작성해주세요.

[문제 링크](https://programmers.co.kr/learn/courses/30/lessons/42588)

### 입출력 예제
> heights	return  
[6,9,5,7,4]	[0,0,2,2,4]  
[3,9,9,3,5,7,2]	[0,0,0,3,3,3,6]  
[1,5,3,6,7,6,5]	[0,0,2,0,0,5,6]  

### 테스트 케이스
```
테스트 1
입력값 〉	[6, 9, 5, 7, 4]
기댓값 〉	[0, 0, 2, 2, 4]

테스트 2
입력값 〉	[3, 9, 9, 3, 5, 7, 2]
기댓값 〉	[0, 0, 0, 3, 3, 3, 6]

테스트 3
입력값 〉	[1, 5, 3, 6, 7, 6, 5]
기댓값 〉	[0, 0, 2, 0, 0, 5, 6]
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
