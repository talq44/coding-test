# 삽입 정렬 (Insertion Sort)
### 설명
- 현재 원소를 알맞은 위치로 삽입하는 방식

### 특징
- 정렬이 거의 되어 있는 경우 O(n)의 시간 복잡도로 매우 빠름.
- **제자리 정렬 (in-place sorting)** 이며, **안정 정렬 (stable sort)**

### 시간 복잡도
- 평균/최악 O(n²)
- 최선 O(n) (이미 정렬된 경우)

### 공간 복잡도
- O(1) (제자리 정렬)

### 장점
- 거의 정렬된 경우 매우 빠름

### 단점
- 큰 데이터셋에서는 비효율적

### Swift 코드
```swift
func insertionSort(_ array: inout [Int]) {
    let n = array.count
    for i in 1..<n {
        var j = i
        while j > 0 && array[j] < array[j - 1] {
            print(i, j, array[j], array[j - 1])
            array.swapAt(j, j - 1)
            j -= 1
        }
    }
}

var numbers = [12, 11, 13, 5, 6]
insertionSort(&numbers)
// 1 1 11 12
// 3 3 5 13
// 3 2 5 12
// 3 1 5 11
// 4 4 6 13
// 4 3 6 12
// 4 2 6 11
print(numbers) // [5, 6, 11, 12, 13]
```