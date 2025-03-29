# 🌐 해시 탐색 (Hash Search) - Set / Dictionary

### 설명
	•	해시 함수를 이용해 키를 해시 테이블의 인덱스로 매핑하여 탐색

### 특징
	•	Swift의 Set, Dictionary가 대표적인 해시 기반 컬렉션

### 시간 복잡도
	•	평균: O(1)
	•	최악: O(n) (충돌 많을 경우)
	•	공간 복잡도: O(n)

### 장점
	•	탐색, 삽입, 삭제가 모두 빠름
	•	중복 체크에 탁월

### 단점
	•	순서 보장 불가
	•	해시 충돌 가능성 존재

### Swift 코드 및 설명
```swift
let names: Set<String> = ["Alice", "Bob", "Charlie"]
print(names.contains("Alice"))  // true
```
	•	Set.contains()는 내부적으로 hash 값을 통해 빠르게 탐색

### iOS 개발에서의 연관성
	•	중복 제거, 빠른 존재 여부 확인, 키-값 매핑
	    •	예: 캐시 처리(NSCache 유사), 이벤트 중복 방지 등