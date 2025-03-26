# O(N²) - 이차 시간 (Quadratic Time)

### 설명
- 입력 크기가 증가할 때, 실행 시간이 N의 제곱(N²)만큼 증가하는 알고리즘
- 이중 루프(중첩된 for-loop)에서 주로 나타남

### 예제
- 버블 정렬(Bubble Sort)
- 선택 정렬(Selection Sort)
- 삽입 정렬(Insertion Sort)
- 대부분의 2중 for 문

### swift 예제
```swift
func bubbleSort(_ arr: inout [Int]) {
    let n = arr.count
    for i in 0..<n {
        for j in 0..<n-i-1 {
            if arr[j] > arr[j+1] {
                arr.swapAt(j, j+1)
            }
        }
    }
}
```