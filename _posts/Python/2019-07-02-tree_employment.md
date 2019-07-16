---
title: "트리순회(tree traversal) 구현"
categories:
  - Python
tags:
  - datastructure
---

### 트리를 활용한 개발

## 코드로 구현해보자
### 트리의 높이
```
Sample Input

     1
      \
       2
        \
         5
        /  \
       3    6
        \
         4  
Sample Output
5
```
```
def height(root):
    level = 0

    # 한 단계 내려갈 때 마다 1을 증가시켜 깊이를 구한다.
    if root :
        if root.left:
            level = height(root.left) + 1
        if root.right:
            level = height(root.right) + 1

    return level
```
