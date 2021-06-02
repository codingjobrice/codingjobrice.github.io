---
layout: single
title: CircularLinkedList
---


원형 연결 리스트는 마지막 노드가 첫번째 노드를 가리키게 함으로써 원처럼 노드가 연결된 자료구조이다.

앞에서의 다른 연결리스트를 보면 head와 tail 이 둘 다 존재 함으로써 위치를 지정했다면 원형 연결리스트는 head 나 tail 둘 중 하나만 있으면 된다.

쓴이는 tail만 있는 원형 연결 리스트를 구현해봤고 아래의 헤더파일과 소스코드를 보면서 ADT를 설명하겠다.


CLinkedList.h


```{.cpp}
typedef struct _node {
	int data;
	struct _node* next;
}Node;

typedef struct _CLL {
	Node* tail;
	Node* cur;
	Node* before;
	int numOfData;
}List;

void ListInit(List* plist);
void LInsert(List* plist, int data);
void LInsertFront(List* plist, int data);

int LFirst(List* plist, int* pdata);
int LNext(List* plist, int* pdata);
int LRemove(List* plist);
int LCount(List* plist);
```

CLinkedList.cpp
```{.cpp}
#include<stdio.h>
#include<stdlib.h>
#include "CLinkedList.h"

void ListInit(List* plist) { //초기화  head가 없다!
	plist->tail = NULL;
	plist->cur = NULL;
	plist->before = NULL;
	plist->numOfData = 0;
}

void LInsertFront(List* plist, int data) { //앞에서 삽입하기
	Node* newNode = (Node*)malloc(sizeof(Node));
	newNode->data = data;

	if (plist->tail == NULL) {
		plist->tail = newNode;
		newNode->next = newNode;
	}
	else {
		newNode->next = plist->tail->next;
		plist->tail->next = newNode;
	}
	(plist->numOfData)++;
}

void LInsert(List* plist, int data) { //뒤에서 삽입하기
	Node* newNode = (Node*)malloc(sizeof(Node));
	newNode->data = data;

	if (plist->tail == NULL) {
		plist->tail = newNode;
		newNode->next = newNode;
	}
	else {
		newNode->next = plist->tail->next;
		plist->tail->next = newNode;
		plist->tail = newNode;
	}
	(plist->numOfData)++;
}

int LFirst(List* plist,int *pdata) {//조회
	if (plist->tail == NULL)
		return false;

	plist->before = plist->tail;
	plist->cur = plist->tail->next;

	*pdata = plist->cur->data;
	return true;
}

int LNext(List* plist, int *pdata) {//조회
	if (plist->tail == NULL)
		return false;

	plist->before = plist->cur;
	plist->cur = plist->cur->next;

	*pdata = plist->cur->data;
	return true;
}

int LRemove(List* plist) {//
	Node* rpos = plist->cur;
	int rdata = rpos->data;

	if (rpos == plist->tail) {
		if (plist->tail == plist->tail->next)
			plist->tail = NULL;
		else
			plist->tail = plist->before;
	}

	plist->before->next = plist->cur->next;
	plist->cur = plist->before;

	free(rpos);
	(plist->numOfData)--;
	return rdata;
}

int LCount(List* plist) {
	return plist->numOfData;
}
```

CLinkedListMain.cpp

```{.cpp}
#include<stdio.h>
#include"CLinkedList.h"

int main() {
	List list;
	int data, i, nodeNum;
	ListInit(&list);

	LInsert(&list, 3);
	LInsert(&list, 4);
	LInsert(&list, 5);
	LInsertFront(&list, 2);
	LInsertFront(&list, 1);

	if (LFirst(&list, &data)) {
		printf("%d ", data);

		for (i = 0; i < LCount(&list) * 3 - 1;i++) {
			if (LNext(&list, &data))
				printf("%d ", data);
		}
	}
	printf("\n");

	nodeNum = LCount(&list);

	if (nodeNum != 0) {
		LFirst(&list, &data);
		if (data % 2 == 0)
			LRemove(&list);
	}
	for (i = 0; i < nodeNum - 1; i++) {
		LNext(&list, &data);
		if (data % 2 == 0)
			LRemove(&list);
	}

	if (LFirst(&list, &data)) {
		printf("%d ", data);

		for (i = 0; i < LCount(&list) - 1; i++) {
			if (LNext(&list, &data)) {
				printf("%d ", data);
			}
		}
	}
}
```
