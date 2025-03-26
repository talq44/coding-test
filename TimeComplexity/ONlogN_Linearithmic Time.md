# O(N log N) - 선형 로그 시간 (Linearithmic Time)

### 설명
- 입력 크기 N에 로그 N을 곱한 형태의 시간 복잡도를 가지며, 대표적으로 정렬 알고리즘에서 많이 나타남

### 예제
- 퀵 정렬(Quick Sort)
- 병합 정렬(Merge Sort)
- 힙 정렬(Heap Sort)

### swift 예제
```swift
func mergeSort(_ arr: [Int]) -> [Int] {
    guard arr.count > 1 else { return arr }
    
    let mid = arr.count / 2
    let left = mergeSort(Array(arr[..<mid]))
    let right = mergeSort(Array(arr[mid...]))
    
    return merge(left, right)
}

func merge(_ left: [Int], _ right: [Int]) -> [Int] {
    var merged = [Int]()
    var leftIndex = 0
    var rightIndex = 0
    
    while leftIndex < left.count && rightIndex < right.count {
        if left[leftIndex] < right[rightIndex] {
            merged.append(left[leftIndex])
            leftIndex += 1
        } else {
            merged.append(right[rightIndex])
            rightIndex += 1
        }
    }
    
    merged.append(contentsOf: left[leftIndex...])
    merged.append(contentsOf: right[rightIndex...])
    
    return merged
}
```