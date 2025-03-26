# O(log N) - 로그 시간 (Logarithmic Time)

### 설명
- 입력이 커질 때, 실행 시간이 로그(log) 형태로 증가하는 알고리즘
- 보통 이진 탐색(Binary Search)처럼 문제를 절반씩 줄여 나가는 방식에서 나타남

### 예제
- 이진 탐색(Binary Search)
- 균형 이진 트리(Balanced Binary Tree)의 삽입 및 삭제
- 힙 정렬

### swift 예제
```swift
func binarySearch(arr: [Int], target: Int) -> Bool {
    var left = 0
    var right = arr.count - 1
    
    while left <= right {
        let mid = left + (right - left) / 2
        if arr[mid] == target {
            return true
        } else if arr[mid] < target {
            left = mid + 1
        } else {
            right = mid - 1
        }
    }
    
    return false
}
```