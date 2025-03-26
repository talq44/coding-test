# 배열

### 개념
- 배열은 연속된 메모리 공간에 데이터를 저장하는 선형 자료구조
- 배열은 고정된 크기(Static Array)와 동적으로 크기가 조정되는 배열(Dynamic Array)이 있다.
- Swift에서는 Array가 동적 배열을 지원

### 동작 방식
- 조회 (O(1)): 인덱스를 통해 특정 원소에 접근 가능
- 삽입 (O(N)): 중간에 삽입 시 뒤 원소들을 이동해야 함
- 삭제 (O(N)): 중간 원소 삭제 시 뒤 원소들을 이동해야 함
- 검색 (O(N)): 순차 검색, 정렬된 배열이라면 이진 탐색(O(logN)) 가능

### 사용 사례
- 유튜브(YouTube), 넷플릭스(Netflix): 영상 목록, 추천 콘텐츠 목록을 배열로 관리
- 게임 개발: 맵 정보 저장 (2D 배열), 캐릭터 위치 업데이트
- 데이터 분석(NumPy, Pandas): 행렬 연산 및 대량 데이터 처리

### 자주 나오는 문제 유형

1. 이진 탐색 (Binary Search)
     - 정렬된 배열에서 특정 값을 빠르게 찾음
     - O(logN)의 시간 복잡도를 가짐
2.	투 포인터 (Two Pointers)
    - 투 포인터는 배열을 정렬된 상태에서 두 개의 포인터를 사용해 특정 조건을 만족하는 값을 찾는 기법
    - 이 방법은 시간 복잡도를 O(N)으로 최적화할 수 있어 효율적인 탐색이 가능
3.	슬라이딩 윈도우 (Sliding Window)
     - 부분 배열의 합, 최댓값을 빠르게 찾을 때 사용
     - 슬라이딩 윈도우 기법은 배열이나 문자열에서 연속된 부분 배열(부분 문자열)의 최적 해를 찾는 문제에 사용
    - 기본적으로 윈도우 크기를 조정하면서 최적 해를 찾으며, 브루트 포스보다 성능을 개선 가능 (O(N) 복잡도).

### Swift 예제

```swift
// 이진 탐색 (Binary Search)
func binarySearch(_ arr: [Int], _ target: Int) -> Int? {
    var left = 0, right = arr.count - 1
    while left <= right {
        let mid = (left + right) / 2
        if arr[mid] == target {
            return mid
        } else if arr[mid] < target {
            left = mid + 1
        } else {
            right = mid - 1
        }
    }
    return nil
}
print(binarySearch([1, 3, 5, 7, 9], 5)) // 출력: 2

// 투 포인터 (Two Pointers)
// 문제: 정렬된 배열에서 합이 target이 되는 두 수의 인덱스를 반환하라.
func twoSumTwoPointers(_ nums: [Int], _ target: Int) -> [Int] {
    var left = 0
    var right = nums.count - 1
    
    while left < right {
        let sum = nums[left] + nums[right]
        if sum == target {
            return [left, right] // 인덱스 반환
        } else if sum < target {
            left += 1 // 합이 작다면 왼쪽 포인터 증가
        } else {
            right -= 1 // 합이 크다면 오른쪽 포인터 감소
        }
    }
    
    return []
}

print(twoSumTwoPointers([1, 2, 3, 4, 6], 6)) // 출력: [1, 3]

// 슬라이딩 윈도우 (Sliding Window)
// 문제: 길이 k의 연속된 부분 배열의 최댓값을 찾아라.
func maxSumSlidingWindow(_ nums: [Int], _ k: Int) -> Int {
    if nums.count < k { return 0 } // 예외 처리

    var windowSum = nums[0..<k].reduce(0, +) // 첫 윈도우의 합
    var maxSum = windowSum

    for i in k..<nums.count {
        windowSum += nums[i] - nums[i - k] // 윈도우를 오른쪽으로 이동
        maxSum = max(maxSum, windowSum)
    }
    
    return maxSum
}

print(maxSumSlidingWindow([2, 1, 5, 1, 3, 2], 3)) // 출력: 9 (5 + 1 + 3)
```

### iOS 개발에서의 연관 관계
- UICollectionView나 UITableView의 dataSource는 보통 Array로 관리됨.
    - 예: 인스타그램 피드, 유튜브 동영상 목록
    - index를 통해 목록의 값을 빠르게 찾아 다음페이지로 이동하는 경우가 많음
    - 최근 선언형 UI에서는 ID로 관리하는 편이며, 때문에 페이지간의 이동은 단순화된 ID를 주고받는 형식을 사용