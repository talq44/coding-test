# 🌊 BFS (Breadth-First Search)

### 설명
	•	가까운 노드부터 차례로 탐색하는 방식
	•	큐(Queue) 를 사용하여 레벨별로 탐색

### 특징
	•	너비 우선
	•	최단 경로 탐색에 적합

### 시간 복잡도
	•	O(V + E)

### 공간 복잡도
	•	O(V) (큐 사용)

### 장점
	•	최단 거리 탐색 보장
	•	무한 루프 없이 탐색 안정적

### 단점
	•	큐에 많은 노드가 들어갈 수 있어 메모리 사용량이 클 수 있음

### Swift 코드 및 설명
```swift
import Foundation
// BFS 구현
func bfs(graph: [[Int]], start: Int) {
    var visited = Array(repeating: false, count: graph.count)
    var queue = [start]
    
    visited[start] = true
    
    while !queue.isEmpty {
        let node = queue.removeFirst()
        print("Visited node: \(node)")
        
        for neighbor in graph[node] {
            if !visited[neighbor] {
                visited[neighbor] = true
                queue.append(neighbor)
            }
        }
    }
}
// 그래프 예시
let graph = [
    [1, 2],
    [0, 3, 4],
    [0, 5],
    [1],
    [1],
    [2]
]
// BFS 호출
bfs(graph: graph, start: 0)
// 출력: Visited node: 0
//        Visited node: 1
//        Visited node: 2
//        Visited node: 3
//        Visited node: 4
//        Visited node: 5


### iOS 개발에서의 연관성
	•	UI 계층의 레벨 순서 탐색, breadth 기반 접근 제어
	    •	예: 네트워크 그래프에서 최단 연결 찾기, 스크롤 가능한 콘텐츠 구조 탐색

### 예시
    •	소셜 네트워크에서 친구 추천
    •	게임 맵 탐색
    •	웹 크롤링
    •	최단 경로 탐색 (예: 최단 거리 찾기)