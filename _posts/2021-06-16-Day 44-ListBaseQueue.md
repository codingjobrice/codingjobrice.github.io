---
layout: single
title: ListBaseQueue
---

연결리스트를 기반으로 한 큐를 작성했다.

배열 기반의 큐는 데이터의 낭비를 막기 위해 원형 큐로 구현해야 했으나 연결리스트 기반의 큐는 그럴 필요가 없다.


아래는 헤더파일과 소스파일이다.



ListBaseQueue.h
```{.cpp}
typedef struct _node {
	int data;
	struct _node* next;
}Node;

typedef struct _lQueue {
	Node* front;
	Node* rear;
}Queue;

void QueueInit(Queue* pq);
int QIsEmpty(Queue* pq);

void Enqueue(Queue* pq, int data);
int Dequeue(Queue* pq);
int QPeek(Queue* pq);

```



ListBaseQueue.cpp
```{.cpp}
#include <stdio.h>
#include <stdlib.h>
#include "ListBaseQueue.h"

void QueueInit(Queue* pq) {
	pq->front = NULL;
	pq->rear = NULL;
}

int QIsEmpty(Queue * pq) {
	if (pq->front == NULL)
		return true;
	else
		return false;
}

void Enqueue(Queue* pq,int data) {
	Node* newNode = (Node*)malloc(sizeof(Node));
	newNode->data = data;
	newNode->next = NULL;
	if (QIsEmpty(pq)) {
		pq->front = newNode;
		pq->rear = newNode;
	}
	else {
		pq->rear->next = newNode;
		pq->rear = newNode;
	}

}

int Dequeue(Queue * pq) {
	Node* delNode;
	int retData;

	if (QIsEmpty(pq)) {
		printf("큐 비어있음\n");
		exit(-1);
	}
	delNode = pq->front;
	retData = delNode->data;
	pq->front = pq->front->next;

	free(delNode);
	return retData;
}
```



ListBaseQueueMain.cpp

```{.cpp}
#include<stdio.h>
#include"ListBaseQueue.h"

int main() {
	Queue q;
	QueueInit(&q);

	Enqueue(&q, 1);
	Enqueue(&q, 2);
	Enqueue(&q, 3);
	Enqueue(&q, 4);
	Enqueue(&q, 5);

	while (!QIsEmpty(&q))
		printf("%d ", Dequeue(&q));
}
```
