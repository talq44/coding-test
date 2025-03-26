# O(N!) - 팩토리얼 시간 (Factorial Time)

### 설명
- 입력 크기가 증가할 때, 실행 시간이 N! (N 팩토리얼)로 증가하는 알고리즘
- 모든 경우의 수를 다 탐색해야 하는 문제에서 발생

### 예제
- 순열(모든 경우의 수 탐색)
- 외판원 문제(Traveling Salesman Problem)

### swift 예제
```swift
func permutations(_ arr: [Int]) -> [[Int]] {
    guard arr.count > 1 else { return [arr] }
    
    var result = [[Int]]()
    
    for i in 0..<arr.count {
        let rest = Array(arr[..<i] + arr[(i+1)...])
        for perm in permutations(rest) {
            result.append([arr[i]] + perm)
        }
    }
    
    return result
}
```