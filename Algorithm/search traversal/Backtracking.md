# 🧩 백트래킹 (Backtracking)

### 설명
	•	가능한 모든 경우를 DFS 방식으로 탐색하며, 조건에 맞지 않으면 이전 상태로 돌아감

### 특징
	•	DFS 기반의 분기 탐색
	•	조건 불만족 시 즉시 되돌아감

### 시간 복잡도
	•	O(2^n) ~ O(n!)
(문제에 따라 조합/순열/경로 탐색 등 다양)

### 공간 복잡도
	•	O(n) (재귀 깊이)

### 장점
	•	모든 가능한 해를 찾을 수 있음
	•	가지치기를 통해 연산량 줄일 수 있음

### 단점
	•	경우의 수가 많으면 매우 느릴 수 있음

### Swift 코드 및 설명 (예: 순열 생성)
```swift
func backtrack(_ nums: [Int], _ path: [Int], _ result: inout [[Int]]) {
    if path.count == nums.count {
        result.append(path)
        return
    }
    
    for i in 0..<nums.count {
        if path.contains(nums[i]) { continue } // 중복 방지
        backtrack(nums, path + [nums[i]], &result)
    }
}
func permute(_ nums: [Int]) -> [[Int]] {
    var result = [[Int]]()
    backtrack(nums, [], &result)
    return result
}
// 사용 예시
let nums = [1, 2, 3]
let permutations = permute(nums)
print(permutations) // [[1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1], [3, 1, 2], [3, 2, 1]]
```

### 예시 문제
1.	[LeetCode 46. Permutations](https://leetcode.com/problems/permutations/)
2.	[LeetCode 77. Combinations](https://leetcode.com/problems/combinations/)
3.	[LeetCode 39. Combination Sum](https://leetcode.com/problems/combination-sum/)
4.	[LeetCode 40. Combination Sum II](https://leetcode.com/problems/combination-sum-ii/)
...


### iOS 개발에서의 연관성
	•	복잡한 옵션 조합 탐색, 사용자 입력 시나리오 제어
	•	예: 입력 폼 유효성 검사, UI 조합 추천, 게임 퍼즐 로직