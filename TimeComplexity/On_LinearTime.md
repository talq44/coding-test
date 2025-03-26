# O(N) - 선형 시간 (Linear Time)

### 설명
- 입력 크기(N)에 비례하여 실행 시간이 증가하는 알고리즘

### 예제
- 배열 전체 탐색 (for-loop)
- 선형 탐색(Linear Search)

### swift 예제
```swift
func linearSearch(arr: [Int], target: Int) -> Bool {
    for num in arr {
        if num == target {
            return true
        }
    }
    return false
}
```