# 큐 (Queue)
### 개념
- 큐(Queue)는 FIFO(First In First Out) 방식으로 동작하는 자료구조이다.

### 동작 방식
- 삽입 (O(1)): enqueue 연산을 통해 맨 뒤에 추가
- 삭제 (O(1)): dequeue 연산을 통해 맨 앞에서 제거
- 탐색 (O(N)): 특정 요소 검색은 순차 탐색 필요

### 사용 사례
- 운영체제(OS) 프로세스 스케줄링: 작업이 FIFO 순서로 실행됨
- 메시지 큐(Kafka, RabbitMQ, AWS SQS): 비동기 데이터 처리
- 네트워크 패킷 큐(Network Routers): 데이터 패킷을 일정한 순서로 처리
- 은행, 티켓팅 시스템: 고객이 먼저 들어온 순서대로 처리됨 (ex: 온라인 예매 대기열)

### 자주 나오는 문제 유형
1.	너비 우선 탐색 (BFS)
2.	캐시 구현 (LRU Cache)
3.	슬라이딩 윈도우 최대값 문제

### Swift 예제
```swift
struct Queue<T> {
    private var elements: [T] = []
    mutating func enqueue(_ element: T) { elements.append(element) }
    mutating func dequeue() -> T? { return elements.isEmpty ? nil : elements.removeFirst() }
}
var queue = Queue<Int>()
queue.enqueue(10)
queue.enqueue(20)
print(queue.dequeue()!) // 10
```

### iOS 개발에서의 연관 관계
- 비동기 작업 관리 (Operation Queue)
    - DispatchQueue 또는 OperationQueue를 사용하여 작업을 FIFO 방식으로 실행
    ```swift
    let queue = DispatchQueue(
        label: "com.app.queue", 
        qos: .background
    )
    
    queue.async {
    // 비동기 네트워크 요청 실행
    }
    ```
- 오프라인 데이터 처리 (CoreData + Batch Processing)
    - 대량의 데이터를 비동기적으로 저장할 때, 큐를 활용하여 순차적으로 처리