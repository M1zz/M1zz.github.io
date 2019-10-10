---
title: "[Programmers_11] 라면공장"
categories:
  - Dailycoding
tags:
  - algorithms
  - heap
---

# 문제
라면 공장에서는 하루에 밀가루를 1톤씩 사용합니다. 원래 밀가루를 공급받던 공장의 고장으로 앞으로 k일 이후에야 밀가루를 공급받을 수 있기 때문에 해외 공장에서 밀가루를 수입해야 합니다.

해외 공장에서는 향후 밀가루를 공급할 수 있는 날짜와 수량을 알려주었고, 라면 공장에서는 운송비를 줄이기 위해 최소한의 횟수로 밀가루를 공급받고 싶습니다.

현재 공장에 남아있는 밀가루 수량 stock, 밀가루 공급 일정(dates)과 해당 시점에 공급 가능한 밀가루 수량(supplies), 원래 공장으로부터 공급받을 수 있는 시점 k가 주어질 때, 밀가루가 떨어지지 않고 공장을 운영하기 위해서 최소한 몇 번 해외 공장으로부터 밀가루를 공급받아야 하는지를 return 하도록 solution 함수를 완성하세요.

dates[i]에는 i번째 공급 가능일이 들어있으며, supplies[i]에는 dates[i] 날짜에 공급 가능한 밀가루 수량이 들어 있습니다.

[문제 링크](https://programmers.co.kr/learn/courses/30/lessons/42629)

### 입출력 예제
> stock	dates	supplies	k	result  
4	[4,10,15]	[20,5,10]	30	2

### 테스트 케이스
```
테스트 1
입력값 〉	4, [4, 10, 15], [20, 5, 10], 30
기댓값 〉	2
```

### 작성 코드 1
```
import heapq

def solution(stock, dates, supplies, k):
    count = 0
    index = 0
    heap = []
    while stock < k:
        # 넣을 수 있는 값 중 가장 큰 값 찾기
        for i in range(index,len(dates)):
            if stock - dates[i] >= 0:
                heapq.heappush(heap,(-supplies[i],supplies[i]))
                index += 1
            else:
                break
        # 공급받기
        stock += heapq.heappop(heap)[1]
        count += 1
    return count
```

### 더 나은 코드 1
```
import heapq

def solution(stock, dates, supplies, k):
    answer, start = 0, 0
    plan = []
    n = len(dates)

    while stock < k:
        for i in range(start, n):
            if dates[i] <= stock:
                heapq.heappush(plan, -supplies[i])
            else:
                start = i
                break
        answer += 1
        stock += -heapq.heappop(plan)
    return answer
```
