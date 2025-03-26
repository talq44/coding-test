# O(2^N) - 지수 시간 (Exponential Time)

### 설명
- 입력 크기가 증가할 때, 실행 시간이 2의 N제곱(2^N)으로 증가하는 알고리즘
- 주로 모든 경우의 수를 탐색하는 알고리즘에서 발생

### 예제
- 피보나치 수열 (재귀적 구현)
- 부분 집합 생성 (Subset Generation)
- 백트래킹 (Backtracking)

### swift 예제
```swift
func fibonacci(_ n: Int) -> Int {
    if n <= 1 { return n }
    return fibonacci(n-1) + fibonacci(n-2)
}
```

⚠️ 해결책: 메모이제이션(Memoization) 기법을 사용하여 O(N)으로 최적화할 수 있음.