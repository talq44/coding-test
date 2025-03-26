# 배열
### 개념
- 연결 리스트는 노드(Node)들이 포인터를 통해 연결된 구조를 가지며, 배열과 달리 메모리상에 연속적으로 존재하지 않아도 된다.

### 동작 방식
- 조회 (O(N)): 순차 탐색이 필요하므로 배열보다 느림
- 삽입/삭제 (O(1)): 포인터만 변경하면 되므로 빠름 (중간 삽입도 효율적)
- 메모리 효율성: 크기가 동적으로 변할 수 있으나, 포인터를 저장하는 공간이 필요함

### 사용 사례
- 운영체제(OS) 메모리 관리: 가변 크기 블록 할당 (예: 페이징 시스템)
- 웹 브라우저(Chrome, Safari) 뒤로/앞으로 가기 기능: 방문한 페이지를 연결 리스트로 저장
- LRU Cache(캐시 구현): 최근 사용한 데이터를 빠르게 갱신하는 데 활용 (ex: Redis, Web Cache)

### 자주 나오는 문제 유형
1. 연결 리스트 반전 (Reverse Linked List)
    - 단방향 연결 리스트의 순서를 뒤집는 문제
    - O(N)
2.	사이클 탐지 (Cycle Detection)
    - Floyd’s Cycle Detection 알고리즘 (빠른/느린 포인터)
    - O(N) 
3.	병합 정렬된 리스트 (Merge Two Sorted Lists)
    - 두 개의 정렬된 연결 리스트를 병합하는 문제
    - O(N)

### Swift 예제

```swift
class ListNode {
    var val: Int
    var next: ListNode?
    init(_ val: Int) {
        self.val = val
        self.next = nil
    }
}

// 연결 리스트 반전
func reverseList(_ head: ListNode?) -> ListNode? {
    var prev: ListNode? = nil
    var curr = head
    while curr != nil {
        let next = curr?.next
        curr?.next = prev
        prev = curr
        curr = next
    }
    return prev
}

// 사이클 탐지 (Cycle Detection)
func hasCycle(_ head: ListNode?) -> Bool {
    var slow = head
    var fast = head

    while fast != nil && fast?.next != nil {
        slow = slow?.next // 한 칸 이동
        fast = fast?.next?.next // 두 칸 이동

        if slow === fast { // 사이클이 존재하는 경우
            return true
        }
    }
    return false
}

// 병합 정렬된 리스트 (Merge Two Sorted Lists)
func mergeTwoLists(_ l1: ListNode?, _ l2: ListNode?) -> ListNode? {
    let dummy = ListNode(0) // 더미 노드 생성
    var current: ListNode? = dummy
    var l1 = l1
    var l2 = l2

    while l1 != nil && l2 != nil {
        if l1!.val < l2!.val {
            current?.next = l1
            l1 = l1?.next
        } else {
            current?.next = l2
            l2 = l2?.next
        }
        current = current?.next
    }

    current?.next = l1 ?? l2 // 남은 노드를 연결

    return dummy.next
}
```

### iOS 개발에서의 연관 관계
- LRU Cache 구현 (메모리 최적화)
    - NSCache와 비슷한 기능을 직접 구현할 때 연결 리스트 + 해시 테이블 활용
    - 최근 사용한 아이템을 빠르게 갱신하기 위해 사용