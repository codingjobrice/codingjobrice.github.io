---
layout: single
title: LinkedListWithDummyNode
---

더미노드를 이용한 연결리스트를 구현했다.

더미노드는 연결리스트의 맨 앞 노드를 빈노드로 설정함으로써 코드를 좀 더 간결하게 할 수 있다. 


자세한 ADT 와 그 설명은 헤더파일과 소스코드를 보면서 설명하겠다.


DLinkedList.h

```{.cpp}
typedef struct _node {
	struct _node* next;
	int data;
}Node;

typedef struct _linkedlist {
	Node* head;
	Node* before;
	Node* cur;
	int numOfData;
	int (*comp)(int d1, int d2);
}List;

void ListInit(List* plist);  
void LInsert(List* plist, int data);

int LFirst(List* plist, int * pdata);
int LNext(List* plist, int* pdata);

int LRemove(List* plist);
int LCount(List* plist);

void SetSortRule(List* plist, int(*comp)(int d1, int d2));
```


DLinkedList.cpp


```{.cpp}
#include <stdio.h>
#include <stdlib.h>
#include"DLinkedList.h"

void ListInit(List* plist) { //초기화
	plist->head = (Node*)malloc(sizeof(Node));
	plist->head->next = NULL;
	plist->comp = NULL;
	plist->numOfData = 0;
}

void FInsert(List* plist, int data) { //삽입1
	Node* newNode = (Node*)malloc(sizeof(Node));
	newNode->data = data;

	newNode->next = plist->head->next;
	plist->head->next = newNode;

	(plist->numOfData)++;
}

void SInsert(List* plist,int data) { //삽입2
	Node* newNode = (Node*)malloc(sizeof(Node));
	Node* pred = plist->head;
	newNode->data = data;

	while (pred->next != NULL && plist->comp(data, pred->data) != 0)
		pred = pred->next;

	newNode->next = pred->next;
	pred->next = newNode;

	(plist->numOfData)++;
}

void LInsert(List* plist,int data) { //삽입1,2
	if (plist->comp == NULL)
		FInsert(plist, data);
	else
		SInsert(plist, data);
}

int LFirst(List* plist,int* pdata) {// 첫번째 노드 조회
	if (plist->head->next == NULL)
		return false;

	plist->before = plist->head;
	plist->cur = plist->head->next;

	*pdata = plist->cur->data;
	return true;
}

int LNext(List* plist, int* pdata) {//두번째 이후 노드 조회
	if (plist->cur->next == NULL) {
		return false;
	}

	plist->before = plist->cur;
	plist->cur = plist->cur->next;

	*pdata = plist->cur->data;
	return true;
}

int LRemove(List* plist) {//삭제
	Node* rpos = plist->cur;
	int rdata = rpos->data;

	plist->before->next = plist->cur->next;
	plist->cur = plist->before;

	free(rpos);
	(plist->numOfData)--;
	return rdata;
}

int LCount(List* plist) { //연결리스트의 노드 갯수 반환
	return plist->numOfData;
}

void SetSortRule(List* plist,int (*comp)(int d1,int d2)) {  //정렬 기준
	plist->comp = comp;
}
```


DLinkedListMain.cpp


```{.cpp}
#include <stdio.h>
#include "DLinkedList.h"

int WhoIsPrecede(int d1, int d2) {//두 수 중에 어떤 수가 앞서는지 판단하여 참,거짓 리턴
	if (d1 < d2)
		return 0;
	else
		return 1;
}

int main() {
	List list;
	int data;
	ListInit(&list);

	SetSortRule(&list, WhoIsPrecede);

	LInsert(&list, 11);
	LInsert(&list, 11);
	LInsert(&list, 22);
	LInsert(&list, 22);
	LInsert(&list, 33);

	printf("현재 데이터 수: %d \n",LCount(&list));

	if (LFirst(&list, &data)) {
		printf("%d ", data);

		while (LNext(&list, &data))
			printf("%d ", data);
	}
	printf("\n\n");

	if (LFirst(&list, &data)) {
		if (data == 22)
			LRemove(&list);

		while (LNext(&list, &data)) {
			if (data == 22)
				LRemove(&list);
		}
	}

	printf("현재 데이터의 수: %d \n", LCount(&list));

	if (LFirst(&list, &data)) {
		printf("%d ", data);

		while (LNext(&list, &data))
			printf("%d ", data);
	}
	printf("\n\n");
}
```


