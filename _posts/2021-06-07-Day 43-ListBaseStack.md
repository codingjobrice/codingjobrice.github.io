---
layout: single
title: ListBaseStack
---

연결리스트를 이용한 스택을 구현했다. 원리는 스택과 같고 단지 연결리스트에서 머리쪽으로 새 노드를 Push하고 머리에서 부터 Pop 하면 스택이 구현된다.


아래의 헤더파일과 소스코드를 보겠다.


ListBaseStack.h

```{.cpp}
typedef struct _node {
	int data;
	struct _node *next;
}Node;

typedef struct _listStack {
	Node* head;
}Stack;

void StackInit(Stack* pstack);
int IsEmpty(Stack* pstack);

void Push(Stack* pstack, int data);
int Pop(Stack* pstack);
int Peek(Stack* pstack);
```

ListBaseStack.cpp

```{.cpp}
#include <stdio.h>
#include "ListBaseStack.h"
#include <stdlib.h>

void StackInit(Stack* pstack) {
	pstack->head = NULL;
}

int IsEmpty(Stack* pstack) {
	if (pstack->head == NULL)
		return true;
	else
		return false;
}

void Push(Stack * pstack, int data) {
	Node* newNode = (Node*)malloc(sizeof(Node));
	newNode->data = data;

	newNode->next = pstack->head;
	pstack->head = newNode;

}

int Pop(Stack* pstack) {
	int rdata;
	Node* rnode;

	if (IsEmpty(pstack)) {
		printf("텅빔\n");
		exit(-1);
	}

	rdata = pstack->head->data;
	rnode = pstack->head;

	pstack->head = pstack->head->next;
	free(rnode);
	return rdata;
}

int Peek(Stack* pstack) {
	if (IsEmpty(pstack)) {
		printf("텅빔\n");
		exit(-1);
	}

	return pstack->head->data;
}
```

ListBaseStackMain.cpp

```{.cpp}
#include <stdio.h>
#include "ListBaseStack.h"

int main() {
	Stack stack;
	StackInit(&stack);

	Push(&stack, 1);
	Push(&stack, 2);
	Push(&stack, 3);
	Push(&stack, 4);
	Push(&stack, 5);

	while (!IsEmpty(&stack))
		printf("%d ", Pop(&stack));
}
```
