# 스택 (Stack)
### 개념
- 스택(Stack)은 LIFO(Last In First Out) 원칙을 따르는 자료구조로, 가장 나중에 삽입된 데이터가 가장 먼저 제거된다.

### 동작 방식
- 삽입 (O(1)): push 연산을 통해 스택의 맨 위에 추가
- 삭제 (O(1)): pop 연산을 통해 스택의 맨 위에서 제거
- 탐색 (O(N)): 특정 원소를 찾으려면 전체를 순회해야 함

### 사용 사례
- 웹 브라우저(Chrome, Firefox) 뒤로 가기 기능: 방문 기록을 스택으로 관리
- 프로그래밍 언어 컴파일러(C, Swift): 함수 호출(재귀 호출)에서 콜 스택 활용
- 문서 편집기(Word, Google Docs): 실행 취소(Undo) 기능 구현

### 자주 나오는 문제 유형
1. 유효한 괄호 문자열 (Valid Parentheses)
2. 스택을 이용한 중위 -> 후위 표기 변환
3. Monotonic Stack을 활용한 Next Greater Element 문제

### Swift 예제

```swift
func isValid(_ s: String) -> Bool {
    var stack: [Character] = []
    let map: [Character: Character] = [")": "(", "}": "{", "]": "["]
    
    for char in s {
        if let expected = map[char], !stack.isEmpty, stack.last == expected {
            stack.popLast()
        } else {
            stack.append(char)
        }
    }
    return stack.isEmpty
}
print(isValid("({[]})")) // true
```

### iOS 개발에서의 연관 관계
- 화면 전환 관리 (Navigation Controller)
    - UINavigationController는 내부적으로 ViewController를 스택 구조로 관리
    ```swift
        navigationController?.pushViewController(nextVC, animated: true)
        navigationController?.popViewController(animated: true)
    ```
