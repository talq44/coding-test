# 🧠 이진 탐색 응용 (Lower Bound / Upper Bound)

### 설명
	•	조건을 만족하는 최소/최대 인덱스를 찾는 이진 탐색의 응용 형태

### 특징
	•	이진 탐색 기반으로 경계 조건에 따라 탐색

### 시간 복잡도
	•	O(log n)

### 장점
	•	조건 만족 범위 찾기에 유리함

### 단점
	•	조건 처리 로직이 복잡할 수 있음

### Swift 코드 및 설명
```swift
func lowerBound(_ arr: [Int], _ target: Int) -> Int {
    var low = 0
    var high = arr.count
    while low < high {
        let mid = (low + high) / 2
        if arr[mid] < target {
            low = mid + 1
        } else {
            high = mid
        }
    }
    return low
}
```
### iOS 개발에서의 연관성
	•	시간 기준 이벤트 필터링, 특정 값 이상인 첫 요소 찾기 등에 활용 가능
	    •	예: 뉴스, 채팅 목록 정렬 후 스크롤 위치 조정