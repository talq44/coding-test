# Swift 내부에서의 정렬 알고리즘
### 설명
Swift의 sorted() 메서드는 내부적으로 Introsort(IntroSort) 알고리즘을 사용합니다.
Introsort는 **퀵 정렬(Quick Sort), 힙 정렬(Heap Sort), 삽입 정렬(Insertion Sort)** 을 조합하여 최적의 성능을 내도록 설계된 정렬 알고리즘입니다.

### Swift의 sorted() 메서드의 내부 동작
Introsort (Introspective Sort)란?

Introsort는 기본적으로 **퀵 정렬(Quick Sort)**을 사용하지만, 다음과 같은 경우 다른 정렬 알고리즘으로 전환됩니다.
- 재귀 깊이가 일정 수준을 넘으면 → **힙 정렬(Heap Sort)** 로 전환 (최악의 경우 O(n log n) 보장)
- 데이터 크기가 작으면 → **삽입 정렬(Insertion Sort)** 로 전환 (작은 데이터에서 빠름)

즉, sorted()는 퀵 정렬을 기반으로 하고, 필요에 따라 힙 정렬과 삽입 정렬을 사용하여 최적의 성능을 보장하는 하이브리드 정렬 알고리즘입니다.

### sorted() vs sort() 차이점
메서드 |	반환값 |	설명
----|----|----
sorted() |	새로운 배열 반환 |	원본 배열을 변경하지 않고 정렬된 새로운 배열을 반환
sort() |	in-place 정렬 |	원본 배열을 직접 정렬

```swift
var numbers = [10, 3, 5, 8, 1, 6]

// 새로운 정렬된 배열을 반환
let sortedNumbers = numbers.sorted()
print(sortedNumbers) // [1, 3, 5, 6, 8, 10]

// 원본 배열을 직접 정렬
numbers.sort()
print(numbers) // [1, 3, 5, 6, 8, 10]
```

### Introsort의 동작 방식 (Swift sorted() 내부 구조)
1.	퀵 정렬(Quick Sort) 사용
    - 일반적으로 퀵 정렬을 사용하여 빠르게 정렬 수행 (평균 O(n log n))
    - 하지만 최악의 경우 O(n²)일 수 있기 때문에 보완책이 필요함.
2.	힙 정렬(Heap Sort)로 전환
    - 퀵 정렬의 재귀 깊이가 log(n)보다 커지면 최악의 경우를 방지하기 위해 **힙 정렬(Heap Sort)** 로 전환.
    - 힙 정렬은 O(n log n)의 시간 복잡도를 보장.
3.	삽입 정렬(Insertion Sort) 적용
    - 데이터 크기가 작으면(16개 이하) 삽입 정렬(Insertion Sort)로 변경하여 성능 최적화.
    - 삽입 정렬은 작은 배열에서 O(n)으로 빠르게 동작.

### Swift의 sorted() 성능 분석
 - 평균 시간 복잡도: O(n log n)
 - 최악 시간 복잡도: O(n log n) (힙 정렬로 대체되므로 O(n²) 방지)
 - 최선 시간 복잡도: O(n) (거의 정렬된 경우 삽입 정렬)

### 성능 테스트 코드
```swift
import Foundation

var largeArray = (1...1000000).shuffled()

let start = Date()
largeArray.sort()  // in-place 정렬
let end = Date()

print("정렬 시간: \(end.timeIntervalSince(start)) 초")
```
결과:
큰 데이터셋에서도 O(n log n) 수준의 성능을 유지함.

### 정리
- sorted()는 **Introsort(퀵 정렬 + 힙 정렬 + 삽입 정렬)** 을 사용.
- 퀵 정렬을 기본으로 사용하지만, 최악의 경우 O(n²)를 방지하기 위해 힙 정렬을 사용.
- 작은 배열의 경우 삽입 정렬로 최적화.
- sort()는 원본 배열을 변경하며, sorted()는 새로운 정렬된 배열을 반환.
- Swift에서 제공하는 sorted()는 일반적으로 가장 최적화된 정렬 알고리즘으로 동작.

즉, Swift의 sorted()는 최악의 경우를 방지하고 빠른 성능을 유지하기 위해 다양한 정렬 알고리즘을 조합한 하이브리드 방식이라고 할 수 있습니다. 🚀