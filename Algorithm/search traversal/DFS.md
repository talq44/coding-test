# 🌐 DFS (Depth-First Search)

### 설명
	•	그래프, 트리 등을 탐색할 때 한 경로를 끝까지 따라가며 탐색하는 방식
	•	재귀 호출 또는 스택을 사용하여 구현

### 특징
	•	깊이 우선
	•	방문 체크 필수 (무한 루프 방지)

### 시간 복잡도
	•	O(V + E)
(V: 정점 수, E: 간선 수)

### 공간 복잡도
	•	O(V) (재귀 깊이 또는 스택 사용)

### 장점
	•	구현이 간단함
	•	백트래킹, 조합, 퍼즐 문제에 적합

### 단점
	•	깊은 그래프에서는 스택 오버플로우 위험 (재귀 기반일 때)
	•	최단 경로를 보장하지 않음

### Swift 코드 및 설명
```swift
import Foundation
// 그래프 클래스 정의
class Graph {
    var adjacencyList: [Int: [Int]] = [:]
    
    func addEdge(_ u: Int, _ v: Int) {
        adjacencyList[u, default: []].append(v)
        adjacencyList[v, default: []].append(u) // 무향 그래프
    }
    
    func dfs(_ start: Int) {
        var visited = Set<Int>()
        dfsHelper(start, &visited)
    }
    
    private func dfsHelper(_ node: Int, _ visited: inout Set<Int>) {
        visited.insert(node)
        print(node) // 방문한 노드 출력
        
        for neighbor in adjacencyList[node, default: []] {
            if !visited.contains(neighbor) {
                dfsHelper(neighbor, &visited)
            }
        }
    }
}
// 그래프 생성 및 엣지 추가
let graph = Graph()
graph.addEdge(1, 2)
graph.addEdge(1, 3)
graph.addEdge(2, 4)
graph.addEdge(2, 5)
graph.addEdge(3, 6)
graph.addEdge(3, 7)
// DFS 탐색 시작
print("DFS Traversal:")
graph.dfs(1)
```
### 설명
    •	그래프를 인접 리스트로 표현
    •	`addEdge` 메서드로 엣지 추가
    •	`dfs` 메서드로 DFS 탐색 시작
    •	`dfsHelper` 메서드에서 재귀적으로 탐색
    •	방문한 노드는 `visited` 집합에 추가하여 중복 방문 방지  

### 예시
```plaintext
DFS Traversal:
1
2
4
5
3
6
7
```

### 참고
    •	DFS는 깊이 우선 탐색으로, 그래프의 모든 정점을 방문하는 데 사용됩니다.
    •	트리 구조에서도 유용하게 사용되며, 경로 탐색, 조합 생성 등 다양한 문제에 활용됩니다.
    •	스택을 사용하여 비재귀적으로 구현할 수도 있습니다.
    •	최단 경로를 찾는 데는 BFS가 더 적합합니다.
    •	DFS는 그래프의 모든 정점을 방문하는 데 사용되며, 경로 탐색, 조합 생성 등 다양한 문제에 활용됩니다.
    •	스택을 사용하여 비재귀적으로 구현할 수도 있습니다.

### iOS 개발에서의 연관성
	•	재귀적으로 UI나 계층 구조를 탐색할 때 (view.subviews, 트리 구조 등)
	•	복잡한 상태머신, 백트래킹 기반 기능 (예: 경로 추천, 게임 로직 등)