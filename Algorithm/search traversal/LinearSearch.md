# 🔍 선형 탐색 (Linear Search)

### 설명
	•	데이터를 처음부터 끝까지 순차적으로 비교하여 원하는 값을 찾는 방식

### 특징
	•	정렬 여부와 상관없이 동작
	•	가장 직관적이고 간단한 탐색

### 시간 복잡도
	•	최악/평균: O(n)
	•	공간 복잡도: O(1)

### 장점
	•	구현이 매우 간단
	•	어떤 형태의 데이터든 적용 가능

### 단점
	•	데이터 양이 많아지면 비효율적

### Swift 코드 및 설명
```swift
// 설명
//    •	`linearSearch` 함수는 배열과 찾고자 하는 값을 인자로 받음
//    •	배열을 순회하면서 각 요소와 타겟 값을 비교
//    •	일치하는 경우 해당 인덱스를 반환하고, 일치하는 값이 없으면 nil 반환
//    •	Swift의 `enumerated()` 메서드를 사용하여 인덱스와 값을 동시에 가져옴
func linearSearch(array: [Int], target: Int) -> Int? {
    for (index, value) in array.enumerated() {
        if value == target {
            return index // 찾은 경우 인덱스 반환
        }
    }
    return nil // 찾지 못한 경우 nil 반환
}
// 사용 예시
let numbers = [5, 3, 8, 6, 2]
let target = 6
if let index = linearSearch(array: numbers, target: target) {
    print("찾은 값의 인덱스: \(index)") // 찾은 값의 인덱스: 3
} else {
    print("값을 찾지 못했습니다.")
}
```

### iOS 개발에서의 연관성
	•	소규모 배열을 필터링하거나 특정 요소를 찾을 때
	    •	예: 특정 뷰 모델 객체 찾기, 특정 조건의 셀 탐색 등