---
layout: single
title: DoublyLinkedList
---

양방향 연결 리스트는 말 그대로 양쪽으로 연결된 자료구조이다.

아래는 헤더파일과 소스파일이다.

DoublyLinkedList.h
```{.cpp}
typedef struct _node {
	int data;
	struct _node* prev;
	struct _node* next;
}Node;

typedef struct _DLinkedList {
	Node* head;
	Node* cur;
	int numOfData;
}List;

void ListInit(List* plist);
void LInsert(List* plist, int data);

int LFirst(List* plist, int* pdata);
int LNext(List* plist, int* pdata);
int LPrevious(List* plist, int* pdata)

int LCount(List* plist);
```


DoublyLinkedList.cpp

```{.cpp}
#include <stdio.h>
#include< stdlib.h>
#include "DBLinkedList.h"

void ListInit(List* plist) {
	plist->head = NULL;
	plist->numOfData = 0;
}

void LInsert(List* plist,int data) {
	Node* newNode = (Node*)malloc(sizeof(Node));
	newNode->data = data;

	newNode->next = plist->head;

	if (plist->head != NULL) {
		plist->head->prev = newNode;
	}

	newNode->prev = NULL;
	plist->head = newNode;

	(plist->numOfData)++;

}

int LFirst(List* plist, int *pdata) {
	if (plist->head == NULL)
		return false;

	plist->cur = plist->head;
	*pdata = plist->cur->data;
	return true;
}

int LNext(List* plist, int* pdata) {
	if (plist->cur->next == NULL)
		return false;

	plist->cur = plist->cur->next;
	*pdata = plist->cur->data;
	return true;
}

int LPrevious(List* plist, int* pdata) {
	if (plist->cur->prev == NULL)
		return false;

	plist->cur = plist->cur->prev;
	*pdata = plist->cur->data;

	return true;
}

int LCount(List* plist) {
	return plist->numOfData;
}
```
