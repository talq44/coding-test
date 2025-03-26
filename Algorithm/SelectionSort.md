# 선택 정렬 (Selection Sort)
### 설명
- 가장 작은 값을 찾아서 앞에서부터 차례로 정렬하는 방식

### 특징
- 항상 O(n²)의 시간 복잡도를 가짐 (최적화가 어려움)
- 교환 횟수가 적어, 메모리 이동 비용이 중요한 경우 유리함
- **제자리 정렬 (in-place sorting)** 이지만, **불안정 정렬 (unstable sort)** 입니다.

### 시간 복잡도
- O(n²) (항상 동일)

### 공간 복잡도
- O(1) (제자리 정렬)

### 장점
- 비교적 코드가 단순함

### 단점
- 다른 효율적인 정렬 알고리즘에 비해 느림

### Swift 코드
```swift
func selectionSort(_ array: inout [Int]) {
    let n = array.count
    for i in 0..<n {
        var minIndex = i
        for j in (i+1)..<n {
            if array[j] < array[minIndex] {
                minIndex = j
            }
        }
        if i != minIndex {
            array.swapAt(i, minIndex)
        }
    }
}

var numbers = [64, 25, 12, 22, 11]
selectionSort(&numbers)
print(numbers) // [11, 12, 22, 25, 64]
```