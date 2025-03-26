# Swift 내부에서의 정렬 알고리즘
## 최근 (2018년 이후)
Swift의 sorted() 및 sort() 메서드는 현재 **TimSort (타임 정렬)** 을 사용합니다.

과거에는 **Introsort(퀵 정렬 + 힙 정렬 + 삽입 정렬)** 이 사용되었지만, 최근 Swift 표준 라이브러리에서는 TimSort로 변경되었습니다.

---

### 📌 TimSort란?

**TimSort(타임 정렬)** 은 **삽입 정렬(Insertion Sort) + 병합 정렬(Merge Sort)** 을 조합한 하이브리드 정렬 알고리즘입니다.
💡 Python, Java에서도 기본 정렬 방식으로 사용되며, 이미 부분적으로 정렬된 배열에서 매우 빠르게 동작하는 특징이 있습니다.

--- 

### 📌 TimSort의 동작 방식
	1.	Runs(런) 탐색
	    - 배열을 작은 정렬된 부분(런, Run)으로 나눕니다.
	    - 만약 배열 내에 이미 정렬된 부분이 있다면, 이를 하나의 “런”으로 인식하여 활용합니다.
	2.	삽입 정렬 적용 (작은 부분 정렬)
	    - 작은 “런”을 정렬할 때는 **삽입 정렬(Insertion Sort)**을 사용합니다.
	    - 삽입 정렬은 작은 크기의 배열에서 매우 효율적으로 동작(O(n)).
	3.	병합 정렬 수행 (큰 부분 정렬)
	    - 정렬된 작은 “런”들을 **병합 정렬(Merge Sort)**을 이용해 합칩니다.
	    - 병합 정렬을 기반으로 하기 때문에 **O(n log n)**의 성능을 보장.
	4.	스마트한 병합 전략
	    - 일반적인 병합 정렬보다 불필요한 병합을 최소화하여 성능 최적화.
	    - 특정한 기준을 통해 “런”을 병합할지 말지를 결정함.

---

### 📌 Swift sorted()에서 TimSort 사용

Swift의 sorted() 및 sort() 메서드는 내부적으로 TimSort를 사용합니다.

🚀 Swift 예제 코드
```swift
var numbers = [10, 3, 5, 8, 1, 6]

// 새로운 정렬된 배열을 반환 (sorted() 사용)
let sortedNumbers = numbers.sorted()
print(sortedNumbers) // [1, 3, 5, 6, 8, 10]

// 원본 배열을 정렬 (sort() 사용)
numbers.sort()
print(numbers) // [1, 3, 5, 6, 8, 10]
```

---

### 📌 TimSort vs Introsort 차이점

정렬 알고리즘 |	기본 동작 |	시간 복잡도 |	공간 복잡도 |	특징
-------|-------|-------|-------|-------
Introsort |	퀵 정렬 + 힙 정렬 + 삽입 정렬 |	O(n log n) | (최악 O(n log n)) |	O(log n)	|퀵 정렬 기반, 힙 정렬로 보완
TimSort |	삽입 정렬 + 병합 정렬 |	O(n log n) | (최악 O(n log n)) |	O(n) |	이미 정렬된 배열에서 빠름

- 🚀 TimSort는 “부분적으로 정렬된 배열”을 빠르게 정렬하는 데 최적화되어 있음
- 🚀 Introsort는 퀵 정렬 기반으로 최악의 경우 힙 정렬을 사용하여 성능을 보장

--- 

### 📌 sorted()가 TimSort를 사용하는 이유
	1.	부분적으로 정렬된 데이터에서 매우 빠름
	    - 실제 데이터는 완전히 무작위가 아니라, 어느 정도 정렬된 경우가 많음.
	    - TimSort는 기존의 정렬된 “런”을 활용하므로 더 효율적.
	2.	안정 정렬 (Stable Sort)
	    - TimSort는 안정 정렬이므로, 같은 값의 상대적인 순서가 유지됨.
	    - 반면, Introsort는 불안정 정렬(unstable)임.
	3.	O(n log n) 성능 보장
	    - 최악의 경우에도 O(n log n) 성능을 유지.

--- 

### 📌 정리
 - ✅ Swift의 sorted()와 sort()는 TimSort를 사용한다.
 - ✅ TimSort는 삽입 정렬 + 병합 정렬을 결합한 하이브리드 정렬 알고리즘이다.
 - ✅ 부분적으로 정렬된 데이터에서 훨씬 빠른 성능을 보인다.
 - ✅ Python, Java에서도 TimSort를 기본 정렬 알고리즘으로 사용 중.
 - ✅ sorted()는 새로운 배열을 반환, sort()는 기존 배열을 정렬.

💡 Swift의 sorted()는 최신 TimSort 기반 정렬 방식을 사용하므로, 일반적으로 최적의 성능을 제공합니다! 🚀


## 과거 (2018년 이전)

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