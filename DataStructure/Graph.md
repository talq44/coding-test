# 그래프(Graph)
### 개념
- 그래프는 **노드(Vertex)와 간선(Edge)** 으로 구성된 자료구조로, 복잡한 관계를 표현하는 데 유용하다.
- 트리와 달리 사이클이 존재할 수 있고, 연결되지 않은 노드가 있을 수도 있다.

### 동작 방식

### 사용 사례
- 소셜 네트워크(Facebook, Instagram, Twitter): 친구 관계 그래프 표현
- 구글 맵(Google Maps, Waze): 최단 경로 찾기 (다익스트라 알고리즘)
- 네트워크 라우팅(BGP, OSPF): 최적의 데이터 전송 경로 탐색
- 추천 시스템(Netflix, Amazon): 유사한 사용자/아이템 추천 (Collaborative Filtering)

### 자주 나오는 문제 유형
1.	BFS (너비 우선 탐색, O(V+E))
    - **큐(Queue)** 를 이용해 레벨 단위로 탐색.
    - 최단 경로 문제에 자주 사용됨.
2.	DFS (깊이 우선 탐색, O(V+E))
    - **재귀(Recursion) 또는 스택(Stack)** 을 사용하여 깊이 우선 탐색.
    - 그래프에서 연결 요소(Connected Components) 찾을 때 사용됨.
### Swift 예제
```swift
class Graph {
    var adjList: [Int: [Int]] = [:]

    func addEdge(_ from: Int, _ to: Int) {
        adjList[from, default: []].append(to)
        adjList[to, default: []].append(from) // 무방향 그래프
    }

    func bfs(_ start: Int) {
        var visited: Set<Int> = []
        var queue: [Int] = [start]

        while !queue.isEmpty {
            let node = queue.removeFirst()
            if visited.contains(node) { continue }
            
            print(node, terminator: " ")
            visited.insert(node)
            queue.append(contentsOf: adjList[node] ?? [])
        }
    }

    func dfs(_ node: Int, _ visited: inout Set<Int>) {
        if visited.contains(node) { return }
        
        print(node, terminator: " ")
        visited.insert(node)

        for neighbor in adjList[node] ?? [] {
            dfs(neighbor, &visited)
        }
    }
}

// 테스트
let graph = Graph()
graph.addEdge(1, 2)
graph.addEdge(1, 3)
graph.addEdge(2, 4)
graph.addEdge(3, 5)

print("BFS 탐색 결과:")
graph.bfs(1) // 출력: 1 2 3 4 5

print("\nDFS 탐색 결과:")
var visited: Set<Int> = []
graph.dfs(1, &visited) // 출력: 1 2 4 3 5
```

### iOS 개발에서의 연관 관계
- 예시들이 적절하지 않은듯 하다.