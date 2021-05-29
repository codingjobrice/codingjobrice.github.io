---
layout: single
title: CircularQueue-Hard
---

큐는 먼저 들어간 것이 먼저 나온다는 개념의 자료구조이다. First In First Out 으로 FIFO 라고도 하며 쓴이는 줄 서는 것에 비유한다. 먼저 줄 선 사람이 먼저 입장하는 원리라고 보면 된다.


큐를 구현하는데 스택과 다르게 원형큐로 구현하는 이유는 데이터가 삭제될 때 비어지는 공간을 다시 사용하게 하기 위해서이다. 


첫 칸을 비우는 이유는 front와 rear 의 위치에 따라 큐가 가득 찼는지 비었는지 구분하기 위해서이다.


원형큐의 ADT는 아래의 헤더파일과 함수들을 보면서 설명하겠다.


CircularQueue.h

```{.cpp}
#define SIZE 100

typedef struct _queue {
	int front;
	int rear;
	int queArr[SIZE];
}Queue;

void QueueInit(Queue * pq);
int IsEmpty(Queue * pq);

void Enqueue(Queue* pq, int data);
int Dequeue(Queue* pq);
```


CircularQueue.cpp

```{.cpp}
#include<stdio.h>
#include"CircularQueue.h"

void QueueInit(Queue * pq) { //큐의 초기화, front 와 rear 을 0으로 초기화한다. 이 때 front == rear 이면 텅 빈 경우임을 알 수 있다.
	pq->front = 0;
	pq->rear = 0;
}

int IsEmpty(Queue * pq) {
	if (pq->front == pq->rear) { //위의 설명에 따라 비었을때 true 를 리턴해주는 함수이다.
		return true;
	}
	else
		return false;
}

int NextPosIdx(int pos) { //다음 인덱스를 리턴함으로써 pos == size-1 이면 가득 찬 상태임을 알 수 있고 가득 차지 않은 경우 +1 을 해준다.
	if (pos == SIZE - 1)
		return 0;
	else
		return pos + 1;
}

void Enqueue(Queue * pq,int data) {
	if (NextPosIdx(pq->rear) == pq->front) {  //큐가 꽉 찼다면
		printf("큐 가득참\n");
	}
	else {
		pq->rear = NextPosIdx(pq->rear); //front 가 0부터 시작했기 때문에 첫 칸은 비우므로 +1 한 후 첫 번째 부터 채우는 것을 보여준다.
		pq->queArr[pq->rear] = data;
	}
}

int Dequeue(Queue * pq) {
	if (IsEmpty(pq)) {
		printf("큐 텅빔\n");
	}
	else {
		pq->front = NextPosIdx(pq->front);
		return pq->queArr[pq->front];
	}
}
```

CircularQueueMain.cpp

```{.cpp}
#include <stdio.h>
#include "CircularQueue.h"

int main() {
	Queue q;
	QueueInit(&q);

	Enqueue(&q, 1);
	Enqueue(&q, 2);
	Enqueue(&q, 3);
	Enqueue(&q, 4);

	while (!IsEmpty(&q)) {
		printf("%d ", Dequeue(&q));
	}

}
```
