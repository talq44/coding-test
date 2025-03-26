# O(1) - 상수 시간 (Constant Time)
### 설명
- 입력 크기(N)와 무관하게 항상 일정한 시간이 걸리는 알고리즘

### 예제
- 배열의 특정 인덱스 접근
- 스택에서 push() 또는 pop()
- 해시 테이블(딕셔너리)의 키 값 조회

### swift 예제
```swift
func getFirstElement(arr: [Int]) -> Int? {
    return arr.first  // O(1)
}
```