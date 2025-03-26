# 해시 테이블 (Hash Table)
### 개념
- 해시 테이블은 키-값(Key-Value) 쌍을 저장하는 자료구조로, 해시 함수를 사용해 데이터를 저장하고 검색한다.

### 동작 방식
- 삽입 (O(1)): 해시 함수를 사용하여 저장
- 삭제 (O(1)): 키 값을 기반으로 삭제
- 탐색 (O(1)): 키를 통해 빠르게 조회 가능 (충돌 시 O(N))

### 사용 사례
- 검색 엔진(Google, Bing): 키워드 검색을 빠르게 수행
- 데이터베이스(Indexing): 빠른 데이터 조회 (ex: MySQL, MongoDB)
- 블록체인(Bitcoin, Ethereum): 거래 데이터 검증 (Merkle Tree)
- 비밀번호 저장(Salted Hashing): 보안 강화를 위해 해싱된 비밀번호 저장

### 자주 나오는 문제 유형
1.	두 수의 합 (Two Sum)
2.	애너그램 그룹핑 (Anagram Grouping)
3.	중복 요소 찾기 (Duplicate Detection)

### Swift 예제
```swift
func twoSum(_ nums: [Int], _ target: Int) -> [Int] {
    var dict = [Int: Int]()
    for (i, num) in nums.enumerated() {
        if let index = dict[target - num] {
            return [index, i]
        }
        dict[num] = i
    }
    return []
}
print(twoSum([2, 7, 11, 15], 9)) // [0, 1]
```

### iOS 개발에서의 연관 관계
- 딕셔너리 기반 데이터 저장
    - JSON 데이터를 Dictionary<String, Any> 형태로 저장하고 접근
    ``` swift
    let json: [String: Any] = ["name": "John", "age": 30]
    print(json["name"] ?? "Unknown")
    ```
- Fast Lookup 기능
    - 앱에서 중복 검색 방지 (Set 활용)
    ```swift
    var visitedPages: Set<String> = []
    if !visitedPages.contains("page1") {
        visitedPages.insert("page1")
    }
    ```