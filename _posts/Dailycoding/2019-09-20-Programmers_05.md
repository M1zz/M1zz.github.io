---
title: "[Programmers_05] 입양 시각 구하기(2)"
categories:
  - Dailycoding
tags:
  - query
  - sql
---

# 문제
보호소에서는 몇 시에 입양이 가장 활발하게 일어나는지 알아보려 합니다. 0시부터 23시까지, 각 시간대별로 입양이 몇 건이나 발생했는지 조회하는 SQL문을 작성해주세요. 이때 결과는 시간대 순으로 정렬해야 합니다.

[문제 링크](https://programmers.co.kr/learn/courses/30/lessons/59413)

### 입출력 예제
> HOUR	COUNT  
0	0  
1	0  
2	0  
3	0  
4	0  
5	0  
6	0  
7	3  
8	1  
9	1  
10	2  
11	13  
12	10  
13	14  
14	9  
15	7  
16	10  
17	12  
18	16  
19	2  
20	0  
21	0  
22	0  
23	0  


### 데이터
```
NAME	TYPE	NULLABLE  
ANIMAL_ID	VARCHAR(N)	FALSE  
ANIMAL_TYPE	VARCHAR(N)	FALSE  
DATETIME	DATETIME	FALSE  
NAME	VARCHAR(N)	TRUE  
SEX_UPON_OUTCOME	VARCHAR(N)	FALSE  
```

### 작성 코드 1
```
SET @hour = -1;
SELECT
    (@hour := @hour +1) as HOUR,
    (SELECT COUNT(*) FROM ANIMAL_OUTS WHERE hour(`datetime`) = @hour) AS `COUNT`
FROM ANIMAL_OUTS
WHERE @hour < 23
```
