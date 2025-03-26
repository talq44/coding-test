# 퀵 정렬 (Quick Sort)
### 설명
- 피벗(Pivot)을 기준으로 작은 값과 큰 값을 분할하여 정렬하는 방식

### 특징
- 평균적으로 **O(n log n)**의 성능을 보이며, 매우 빠름.
- 하지만, 피벗이 최악으로 선택되면 **O(n²)**이 될 수 있음.

### 시간 복잡도
- 평균 O(n log n)
- 최악 O(n²) (pivot 선택이 좋지 않으면)

### 공간 복잡도
- O(log n) (재귀 호출 스택)

### 장점
- 평균적으로 가장 빠름, 추가 공간 필요 없음

### 단점
- 최악의 경우 O(n²) 가능 (pivot 선택이 중요)

### Swift 코드
```swift
func quickSort(_ array: [Int]) -> [Int] {
    guard array.count > 1 else { return array }
    
    let pivot = array[array.count / 2]
    let less = array.filter { $0 < pivot }
    let equal = array.filter { $0 == pivot }
    let greater = array.filter { $0 > pivot }
    
    return quickSort(less) + equal + quickSort(greater)
}

var numbers = [10, 7, 8, 9, 1, 5]
numbers = quickSort(numbers)
print(numbers) // [1, 5, 7, 8, 9, 10]
```