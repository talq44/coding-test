# 트리 (Tree)
### 개념
- 트리는 계층적 구조를 가지며 **노드(Node)와 간선(Edge)** 으로 구성된다.
- 트리는 사이클이 없는 그래프의 한 종류로, 최상위 노드(루트)를 기준으로 여러 개의 자식 노드를 가질 수 있다.

### 동작 방식
- 삽입 (O(logN)): 새로운 노드를 적절한 위치에 삽입.
- 삭제 (O(logN)): 특정 노드를 삭제하고 트리를 재구성.
- 탐색 (O(logN)): 원하는 값을 찾아가는 과정 (BST 기준).
- 순회 (O(N)):
  - 전위 순회 (Preorder): 루트 → 왼쪽 → 오른쪽
  - 중위 순회 (Inorder): 왼쪽 → 루트 → 오른쪽 (BST에서는 정렬된 결과 출력됨)
  - 후위 순회 (Postorder): 왼쪽 → 오른쪽 → 루트

### 사용 사례

### 자주 나오는 문제 유형
1.	이진 트리 (Binary Tree)
    - 각 노드가 최대 2개의 자식(왼쪽, 오른쪽)만 가질 수 있는 트리.
2.	이진 탐색 트리 (Binary Search Tree, BST)
    - 왼쪽 자식은 부모보다 작은 값, 오른쪽 자식은 부모보다 큰 값을 가짐.
    - **탐색이 O(logN)** 으로 빠름 (균형이 맞다면).
3.	AVL 트리 / 레드-블랙 트리
    - 균형을 유지하는 BST (높이 차이가 일정 수준 이하).
4.	힙 (Heap)
    - **완전 이진 트리(Complete Binary Tree)**로, 최댓값 또는 최솟값을 빠르게 찾음.

### Swift 예제
```swift
class TreeNode {
    var val: Int
    var left: TreeNode?
    var right: TreeNode?

    init(_ val: Int) {
        self.val = val
        self.left = nil
        self.right = nil
    }
}

// 이진 탐색 트리 삽입
func insertNode(_ root: TreeNode?, _ val: Int) -> TreeNode? {
    guard let root = root else { return TreeNode(val) }
    
    if val < root.val {
        root.left = insertNode(root.left, val)
    } else {
        root.right = insertNode(root.right, val)
    }
    return root
}

// 중위 순회 (오름차순 정렬 출력)
func inorderTraversal(_ root: TreeNode?) {
    guard let root = root else { return }
    inorderTraversal(root.left)
    print(root.val, terminator: " ")
    inorderTraversal(root.right)
}

// 테스트
var root: TreeNode? = nil
root = insertNode(root, 5)
root = insertNode(root, 3)
root = insertNode(root, 7)
root = insertNode(root, 2)
root = insertNode(root, 4)

inorderTraversal(root) // 출력: 2 3 4 5 7
```

### iOS 개발에서의 연관 관계
- 파일 시스템 탐색 (Document Picker)
    - iOS의 UIDocumentPicker에서 트리 구조로 디렉토리 관리

- 앱 내 메뉴 트리 구조
    - 설정 화면 (예: iOS 설정 앱)
    - 네이버 카테고리 트리 구조

- iOS CoreData Indexing (B+Tree)
    - CoreData는 내부적으로 B+Tree를 사용하여 검색 최적화

- Auto Layout Constraint Solving
    - 레이아웃이 트리 구조로 되어 있어서 Constraint Resolver가 트리 탐색을 수행함