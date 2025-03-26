# 기술면접/코딩테스트 대비를 위한 저장소
- 자주 까먹게 되는 지식을 쉽게 찾기 위해 관리합니다.
- 관련된 코드를 Swift로 구현해 확인합니다.


## 자료구조
- [배열(Array)](https://github.com/talq44/coding-test/blob/main/DataStructure/Array.md)
- [연결 리스트(Linked List)](https://github.com/talq44/coding-test/blob/main/DataStructure/LinkedList.md)
- [스택(Stack)](https://github.com/talq44/coding-test/blob/main/DataStructure/Stack.md)
- [큐(Queue)](https://github.com/talq44/coding-test/blob/main/DataStructure/Queue.md)
- [해시 테이블(Hash Table)](https://github.com/talq44/coding-test/blob/main/DataStructure/HashTable.md)
- [트리(Tree)](https://github.com/talq44/coding-test/blob/main/DataStructure/Tree.md)
- [그래프(Graph)](https://github.com/talq44/coding-test/blob/main/DataStructure/Graph.md)
- [힙(Heap)](https://github.com/talq44/coding-test/blob/main/DataStructure/Heap.md)
- 트라이(Trie)
- 세그먼트 트리(Segment Tree)


## 시간복잡도
![image](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20220812122843/Logarithmic-time-complexity-blog-1.jpg)

복잡도	 | 설명	 | 예제
--------|------------|------------
O(1)	| 입력 크기에 관계없이 일정한 실행 시간 | 	배열의 특정 원소 접근, 딕셔너리 조회
O(log N) |	입력 크기가 커질수록 실행 시간이 느리게 증가 |	이진 탐색(Binary Search)
O(N) |	입력 크기에 비례하여 실행 시간이 증가	| 선형 탐색(Linear Search)
O(N log N)	| 입력 크기가 커질수록 실행 시간 증가 속도가 N보다 빠름 |	퀵 정렬, 병합 정렬
O(N²) |	이중 루프를 사용하여 실행 시간이 기하급수적으로 증가 |	버블 정렬, 선택 정렬
O(2^N) |	모든 경우의 수를 탐색해야 하는 경우	| 피보나치(재귀), 백트래킹
O(N!) |	순열과 같이 모든 경우를 탐색 |	외판원 문제, 순열 생성
