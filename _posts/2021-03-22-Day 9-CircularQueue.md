---
layout: single
title: Day 9 CircularQueue
---

큐(queue)는 FIFO의 구조로 먼저 들어간 것이 먼저 나오는 자료구조이다. 나는 대기 순번을 기다리는 줄에 비유한다. 먼저 온 사람이 먼저 음식을 받는다.

큐를 원형큐의 구조로 하는 이유는 Dequeue 하고 남은 공간이 빈공간으로 사용되지 않고 다시 쓸 수 있게 끔 하기 위해서이다.

```{.cpp}
#include <stdio.h>
#define size 100

int Queue[size];
int front = 0;
int rear = 0;

int IsEmpty() {
	if (front == rear)
		return true;
	else
		return false;
}

int IsFull() {
	if ((rear + 1) % size == front)
		return true;
	else
		return false;
}

void Enqueue(int data) {
	if (IsFull()) {
		printf("가득 참");
	}
	else {
		rear++;
		Queue[rear] = data;
	}
}

void Dequeue() {
	if (IsEmpty())
		printf("텅 빔");
	else {
		front = (front + 1) % size;
		Queue[front] = NULL;
	}
}

int main() {
	Enqueue(1);
	Enqueue(2);
	Enqueue(3);
	Enqueue(4);
	Enqueue(5);
	Dequeue();
	Dequeue();
	Dequeue();

	int i = front+1;

	while (Queue[i] != NULL) {
		printf("%d ", Queue[i]);
		i++;
	}
}
```
