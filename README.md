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

## 알고리즘
### 정렬

- 정렬(Sorting)이란 데이터를 일정한 순서로 배열하는 것을 의미
- 정렬 알고리즘은 효율성을 기준으로 기본 정렬(O(n²)), 효율적인 정렬(O(n log n)), **특수 정렬(O(n))** 로 나눌 수 있음

📌 정렬 알고리즘 종류

알고리즘 |	시간 복잡도 (최선) |	시간 복잡도 (평균) |	시간 복잡도 (최악) |	공간 복잡도 |	특징
-------|--------------|--------------|-------|-------|-------
버블 정렬 (Bubble Sort) |	O(n) |	O(n²) |	O(n²) |	O(1) |	인접한 두 개의 원소를 비교하여 정렬
선택 정렬 (Selection Sort) |	O(n²) |	O(n²) |	O(n²) |	O(1) |	가장 작은 원소를 선택하여 맨 앞에 배치
삽입 정렬 (Insertion Sort) |	O(n) |	O(n²) |	O(n²) |	O(1) |	데이터를 하나씩 정렬된 위치에 삽입
병합 정렬 (Merge Sort) |	O(n log n) |	O(n log n) |	O(n log n) |	O(n) |	분할 정복(Divide & Conquer)
퀵 정렬 (Quick Sort) |	O(n log n) |	O(n log n) |	O(n²) |	O(log n) |	피벗을 기준으로 분할하여 정렬
계수 정렬 (Counting Sort) |	O(n + k) |	O(n + k) |	O(n + k) |	O(k) |	숫자의 빈도를 활용한 정렬
