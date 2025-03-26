# 병합 정렬 (Merge Sort)
### 설명
- 분할 정복(Divide and Conquer) 기법을 사용하여 리스트를 반으로 나눈 후, 각각을 정렬한 뒤 합치는 방식

### 특징
- 항상 **O(n log n)** 의 성능을 보장.
- **안정 정렬 (stable sort)** 이지만, 추가적인 메모리 공간이 필요함.

### 시간 복잡도
- O(n log n) (항상 동일)

### 공간 복잡도
- O(n) (보조 배열 필요)

### 장점
- 안정 정렬(Stable Sort), 큰 데이터셋에서도 안정적인 성능

### 단점
- 추가적인 공간이 필요함

### Swift 코드
```swift
func mergeSort(_ array: [Int]) -> [Int] {
    guard array.count > 1 else { return array }
    
    let mid = array.count / 2
    let left = mergeSort(Array(array[..<mid]))
    let right = mergeSort(Array(array[mid...]))
    
    return merge(left, right)
}

func merge(_ left: [Int], _ right: [Int]) -> [Int] {
    var sortedArray = [Int]()
    var leftIndex = 0, rightIndex = 0
    
    while leftIndex < left.count && rightIndex < right.count {
        if left[leftIndex] < right[rightIndex] {
            sortedArray.append(left[leftIndex])
            leftIndex += 1
        } else {
            sortedArray.append(right[rightIndex])
            rightIndex += 1
        }
    }
    
    return sortedArray + left[leftIndex...] + right[rightIndex...]
}

var numbers = [38, 27, 43, 3, 9, 82, 10]
numbers = mergeSort(numbers)
print(numbers) // [3, 9, 10, 27, 38, 43, 82]
```