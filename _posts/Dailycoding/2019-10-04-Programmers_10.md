---
title: "[Programmers_10] 더 맵게"
categories:
  - Dailycoding
tags:
  - algorithms
  - queue
---

# 문제
매운 것을 좋아하는 Leo는 모든 음식의 스코빌 지수를 K 이상으로 만들고 싶습니다. 모든 음식의 스코빌 지수를 K 이상으로 만들기 위해 Leo는 스코빌 지수가 가장 낮은 두 개의 음식을 아래와 같이 특별한 방법으로 섞어 새로운 음식을 만듭니다.

>섞은 음식의 스코빌 지수 = 가장 맵지 않은 음식의 스코빌 지수 + (두 번째로 맵지 않은 음식의 스코빌 지수 * 2)

Leo는 모든 음식의 스코빌 지수가 K 이상이 될 때까지 반복하여 섞습니다.
Leo가 가진 음식의 스코빌 지수를 담은 배열 scoville과 원하는 스코빌 지수 K가 주어질 때, 모든 음식의 스코빌 지수를 K 이상으로 만들기 위해 섞어야 하는 최소 횟수를 return 하도록 solution 함수를 작성해주세요.

[문제 링크](https://programmers.co.kr/learn/courses/30/lessons/42626)

### 입출력 예제
> scoville	K	return  
[1, 2, 3, 9, 10, 12]	7	2

### 테스트 케이스
```
테스트 1
입력값 〉	[1, 2, 3, 9, 10, 12], 7
기댓값 〉	2
```

### 작성 코드 1
```
def solution(scoville, K):
    hot = scoville[:]
    count = 0
    while min(hot) <= K:
        hot.sort()
        try:
            hot.append(hot.pop(0) + hot.pop(0)*2)
        except IndexError:
            return -1
        count += 1
    if count == len(scoville):
        return -1
    else:
        return count
```
실행시간 극복 불가
### 작성 코드 2
```
import heapq
def solution(scoville, K):
    count = 0
    heap = []
    for num in scoville:
        heapq.heappush(heap,num)

    while heap[0] <= K:
        try:
            heapq.heappush(heap, heapq.heappop(heap)+heapq.heappop(heap)*2)
        except IndexError:
            return -1
        count += 1
    if count == len(scoville):
        return -1
    else:
        return count
```
### 더 나은 코드 1
```
import heapq as hq

def solution(scoville, K):
    hq.heapify(scoville)
    answer = 0
    while True:
        first = hq.heappop(scoville)
        if first >= K:
            break
        if len(scoville) == 0:
            return -1
        second = hq.heappop(scoville)
        hq.heappush(scoville, first + second*2)
        answer += 1  

    return answer
```
