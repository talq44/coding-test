# Set

### 기본 동작
- Set에 값을 넣으면 해당 값의 **해시값(hashValue)** 를 이용해 내부 저장소 위치를 결정합니다.
- 값의 중복을 허용하지 않음 → 중복 삽입 시 무시됨
- 값의 순서가 없음 → 입력 순서와 출력 순서가 다를 수 있음

### 요구 조건
- Set에 넣을 타입은 반드시 Hashable을 채택해야 함.
- 예: Int, String, Double, Bool, enum, struct(Hashable 채택한 경우)
```swift
var fruits: Set<String> = ["apple", "banana", "orange"]

fruits.insert("mango")     // 삽입
fruits.contains("apple")   // 탐색 → O(1)
fruits.remove("banana")    // 삭제 → O(1)
```

### ⚙️ 내부 동작 방식 (간단히 설명)
1.	insert("apple") 호출 시:
    - "apple".hashValue를 계산
    - 이 값을 바탕으로 버킷(bucket) 위치 결정
    - 해당 위치가 비어있다면 저장
    - 아니면 충돌 처리 (Open Addressing 또는 Separate Chaining 방식)
2.	contains("apple") 호출 시:
    - 동일한 방식으로 hashValue → 버킷 위치 계산
    - 해당 버킷을 바로 확인해서 존재 여부 판단

### 🆚 Set vs Array vs Dictionary 탐색 성능

컬렉션 |	평균 탐색 시간  |	특징
-----|--------------------|-----
Array   |	O(n)    |	순차 탐색
Set |	O(1)    |	해시 기반, 중복 없음
Dictionary  |	O(1)    |	key-value 구조, 해시 기반


### 🎯 정리

항목    |	Swift의 Set
-----|-----
구조    |	Hash Table
탐색 성능   |	평균 O(1), 최악 O(n) (충돌 발생 시)
중복 허용 여부  |	❌ 불가능
순서 보장   |	❌ 없음
요구 조건   |	요소는 Hashable을 따라야 함