---
layout: single
title: LinkedList(Easy)
---

연결리스트는 배열의 메모리 특성이 정적인 것을 동적으로 구성하기 위해 동적 할당을 하는 배열로 볼 수 있다.

크게 노드의 구현, 삽입, 조회, 삭제 4가지 단계로 구성해 코드로 표현했다.

```{.cpp}
#include <stdio.h>
#include <malloc.h>

//노드의 구현
typedef struct _node {
	int data;
	struct _node* next;
}Node;

int main() {
	Node* head = NULL;
	Node* tail = NULL;
	Node* cur = NULL;

	Node* newNode = NULL;
	int readData;

	while (1) { 
    //데이터 삽입
		printf("데이터 입력: ");
		scanf_s("%d", &readData);
		if (readData < 1)
			break;

		newNode = (Node*)malloc(sizeof(Node));
		newNode->data = readData;
		newNode->next = NULL;

		if (head == NULL)
			head = newNode;
		else
			tail->next = newNode;

		tail = newNode;
	}
	printf("\n");
  //데이터 조회
	printf("데이터 조회\n");

	if (head == NULL) {
		printf("데이터 없음\n");
	}
	else {
		cur = head;
		printf("%d ", cur->data);
		
		while (cur->next != NULL) {
			cur = cur->next;
			printf("%d ", cur->data);
		}
	}
	printf("\n\n");
  
  //데이터 
	printf("데이터 삭제\n");

	if (head == NULL)
		return 0;
	else {
		Node* dn = head;
		Node* dnn = head->next;

		printf("%d 를 삭제합니다.\n", head->data);
		free(dn);

		while (dnn != NULL) {
			dn = dnn;
			dnn = dnn->next;

			printf("%d 를 삭제합니다.\n", dn->data);
			free(dn);
		}
	}
}
```
