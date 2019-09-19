---
title: "[Programmers_04] 위장"
categories:
  - Dailycoding
tags:
  - algorithms
  - hash
---

# 문제
스파이들은 매일 다른 옷을 조합하여 입어 자신을 위장합니다.

예를 들어 스파이가 가진 옷이 아래와 같고 오늘 스파이가 동그란 안경, 긴 코트, 파란색 티셔츠를 입었다면 다음날은 청바지를 추가로 입거나 동그란 안경 대신 검정 선글라스를 착용하거나 해야 합니다.

종류	이름  
얼굴	동그란 안경, 검정 선글라스  
상의	파란색 티셔츠  
하의	청바지  
겉옷	긴 코트  

스파이가 가진 의상들이 담긴 2차원 배열 clothes가 주어질 때 서로 다른 옷의 조합의 수를 return 하도록 solution 함수를 작성해주세요.

[문제 링크](https://programmers.co.kr/learn/courses/30/lessons/42578)

### 입출력 예제
> clothes	return  
[[yellow_hat, headgear], [blue_sunglasses, eyewear], [green_turban, headgear]]	5  
[[crow_mask, face], [blue_sunglasses, face], [smoky_makeup, face]]	3  


### 테스트 케이스
```
테스트 1
입력값 〉	[["yellow_hat", "headgear"], ["blue_sunglasses", "eyewear"], ["green_turban", "headgear"]]
기댓값 〉	5

테스트 2
입력값 〉	[["crow_mask", "face"], ["blue_sunglasses", "face"], ["smoky_makeup", "face"]]
기댓값 〉	3
```

### 작성 코드 1
```
import collections
def solution(clothes):

    temp = []
    for item in clothes:
        temp.append(item[1])
    count = dict(collections.Counter(temp))
    print (count)
    total = 1
    for item in count:
          total = total * (count[item]+1)
    return total - 1
```


### 더 나은 코드 1
```
def solution(clothes):
    from collections import Counter
    from functools import reduce
    cnt = Counter([kind for name, kind in clothes])
    answer = reduce(lambda x, y: x*(y+1), cnt.values(), 1) - 1
    return answer
```
