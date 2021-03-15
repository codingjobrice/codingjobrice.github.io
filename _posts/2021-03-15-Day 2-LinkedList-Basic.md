---
layout: single
tiltle: "연결리스트 기초 구현"
---

자료구조도 공부하게 되면서 올립니다... 기본 연결리스트이며 함수화 시켜 좀 더 간단하게 나타내는 건 다음에 하겠습니다.

```{.cpp}
#include <stdio.h>
#include <malloc.h>

typedef struct _Node {
	int data;
	_Node* next;
}Node;

int main() {
	//head, node1,2,3 동적할당 후 데이터를 삽입해줍니다.
	Node* head = (Node*)malloc(sizeof(Node));
	Node* node1 = (Node*)malloc(sizeof(Node));
	Node* node2 = (Node*)malloc(sizeof(Node));
	Node* node3 = (Node*)malloc(sizeof(Node));

	node1->data = 1;
	node2->data = 2;
	node3->data = 3;

	//head 는 node1 을 가리키고 node들도 순서대로 가리키게 해줍니다.
	head->next = node1;
	node1->next = node2;
	node2->next = node3;
	node3->next = NULL;

	//cur을 head->next로 초기화 시켜 cur을 한 노드씩 이동하며 가리켜 출력시켜줍니다.  
	Node* cur = head->next;
	printf("삭제 전 노드 참조:\n");
	while (cur!= NULL) {
		printf("%d\n", cur->data);
		cur = cur->next;
	}

	//node2 삭제하며 node2 의 다음 노드 였던 node3를 node1->next로 설정 해준 다음 node2를 메모리 해제 해줍니다.
	node1->next = node3;
	free(node2);

	cur = head->next;
	printf("삭제 후 노드 참조:\n");
	while (cur != NULL) {
		printf("%d\n", cur->data);
		cur = cur->next;
	}

	free(head);
	free(node1);
	free(node3);
}
```
