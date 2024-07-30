Date: 2024-07-29

## 재귀 함수(Rexursive Function)
자기 자신을 다시 호출하는 함수로, 종료 조건을 반드시 필요로 함
재귀 함수는 수학의 점화식을 그대로 소스 코드로 옮겨 코드가 간단하고 이 개념은 다이나믹 프로그래밍으로 이어짐  
컴퓨터 내부에서 재귀함수는 스택 자료구조를 활용함  

## DFS
**그래프**: Node, Edge로 표현되며 인접 행렬, 인접 리스트 방식으로 표현할 수 있음  
**인접 행렬**: 2차원 배열에 각 노드가 연결된 형태 기록하는 방식  
Edge로 연결되지 않은 노드 간은 INF를 사용함  
**인접 리스트**: Linked List를 사용해 구현하나, Python은 기존 list가 이러한 형태로 이루어짐  
```python
graph = [[] for _ in range(3)]

# 노드 0에 연결된 노드 정보(노드, 거리)
graph[0].append((1, 7))
graph[0].append((2, 5))
```
위와 같이 구현해 사용  
**인접 행렬 VS 인접 리스트**: 인접 행렬 방식에 비해 인접 리스트는 불필요한 메모리 사용이 적으나 특정 두 노드간의 관계를 살피기에는 속도가 느림  
따라서 하나의 특정 노드에 연결된 모든 노드를 순회할 때는 인접 리스트의 메모리 공간 낭비가 적음  

재귀를 사용한 예제 소스코드) 
```python
def dfs(graph, v, visited):
    visited[v] = True
    print(v, end=' ')
    for i in graph[v]:
        if not visited[i]:
            dfs(graph, i, visited)

graph = [
    # 각 노드에 연결된 노드 list 따라서 0은 비워둠
    [],
    [2, 3, 8],
    [1, 7],
    [1, 4, 5],
    [3, 5],
    [3, 4],
    [7],
    [2, 6, 8],
    [1, 7]
]

visited = [False] * 9

dfs(graph, 1, visited)
```
이 때 탐색 순서는 스택에 들어간 순서(재귀 호출 v 순서)

## BFS  
가까운 노드부터 탐색하는 알고리즘  
DFS는 먼 것부터 탐색하기 때문에(한 방향으로 쭉 내려감) 인접한 노드 중 가장 작은 값부터 하나씩 탐색하지만  
BFS는 가까운 노드부터 탐색하므로 인접한 노드를 한꺼번에 queue에 삽입함  
deque 라이브러리를 사용해 구현할 수 있으며, 탐색 시간이 ```O(N)```으로 일반적으로 DFS보다 좋음  

BFS 예제)
```python  
from collections import deque

def bfs(graph, start, visited):
    queue = deque([start])
    visited[start] = True
    while queue:
        # 기존 node를 pop하고 인접 노드를 삽입
        v = queue.popleft()
        print(v, end=' ')
        for i in graph[v]:
            if not visited[i]:
                queue.append(i)
                visited[i] = True

graph = [
    [],
    [2, 3, 8],
    [1, 7],
    [1, 4, 5],
    [3, 5],
    [3, 4],
    [7],
    [2, 6, 8],
    [1, 7]
]

visited = [False] * 9
bfs(graph, 1, visited)
```

## DFS/BFS 실전 문제 풀이
boj 1260(Algorithm repository 참고)를 풀면서 여러 반례를 접하고 깨달은 점  
* list(set(arr))을 해준 다음에 sort()를 해주어야 함  
* print(a, end=' ')를 사용해 한 줄에 출력할 수 있어 굳이 array를 사용하지 않아도 되서 메모리를 아낄 수 있음  
* print('')을 사용해 출력 줄을 구분할 수 있음
* 문제를 풀면서 기본적인 원리를 제대로 이해할 수 있었음  
