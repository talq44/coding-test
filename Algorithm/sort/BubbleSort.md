# 버블 정렬 (Bubble Sort)
### 설명
- 인접한 두 개의 원소를 비교하여 정렬하는 방식
- 가장 큰 원소가 맨 끝으로 이동하는 것이 특징

### 특징
- 정렬이 거의 되어 있는 경우, O(n)으로 동작하여 빠름.
- 하지만 일반적으로 O(n²)의 성능을 가지므로 비효율적.
- **제자리 정렬 (in-place sorting)** 이며, **안정 정렬 (stable sort)**

### 시간 복잡도
- 평균/최악 O(n²)
- 최선 O(n) (이미 정렬된 경우)

### 공간 복잡도
- O(1) (제자리 정렬)

### 장점
- 코드가 단순하고 이해하기 쉬움

### 단점
- 데이터가 많을수록 비효율적

### Swift 코드
```swift
func bubbleSort(_ array: inout [Int]) {
    let n = array.count
    for i in 0..<n {
        var swapped = false
        for j in 0..<(n - i - 1) {
            if array[j] > array[j + 1] {
                print(i, j, array[j], array[j + 1]) // 변경 순서를 보기 위한 print
                array.swapAt(j, j + 1)
                swapped = true
            }
        }
        if !swapped { break } // 더 이상 교환이 발생하지 않으면 종료
    }
}

var numbers = [5, 2, 9, 1, 5, 6]
bubbleSort(&numbers)
// 0 0 5 2
// 0 2 9 1
// 0 3 9 5
// 0 4 9 6
// 1 1 5 1
// 2 0 2 1
print(numbers) // [1, 2, 5, 5, 6, 9]
```