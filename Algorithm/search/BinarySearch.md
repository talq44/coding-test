2. 🔎 이진 탐색 (Binary Search)

### 설명
	•	정렬된 배열을 전제로, 중간 값을 기준으로 절반씩 범위를 줄여가며 탐색

### 특징
	•	탐색 속도가 매우 빠름
	•	정렬된 데이터만 사용 가능

### 시간 복잡도
	•	최악/평균: O(log n)
	•	공간 복잡도: O(1) (반복문), O(log n) (재귀)

### 장점
	•	탐색 효율이 매우 좋음

### 단점
	•	정렬되지 않은 데이터에는 사용할 수 없음

### Swift 코드 및 설명
```swift
func binarySearch(_ arr: [Int], _ target: Int) -> Int? {
    var low = 0
    var high = arr.count - 1
    
    while low <= high {
        let mid = (low + high) / 2
        if arr[mid] == target {
            return mid
        } else if arr[mid] < target {
            low = mid + 1
        } else {
            high = mid - 1
        }
    }
    return nil
}
```
	•	중간 값을 기준으로 범위를 나눠가며 탐색하는 방식

### iOS 개발에서의 연관성
	•	정렬된 데이터 모델에서 특정 요소를 빠르게 탐색할 때
	    •	예: 날짜 순으로 정렬된 이벤트에서 특정 날짜 찾기 등