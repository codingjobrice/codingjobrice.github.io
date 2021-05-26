---
layout: single
title: Stack_Completed
---

스택을 구현한 글이 이전에 있었으나 스택을 전역변수가 아닌 헤더파일을 이용하여 좀 더 체계적으로 구현했다.


스택은 LIFO의 구조로 먼저 들어간 것이 나중에 나오는 자료구조이다.

글쓴이는 프링글스 통에 비유하며 먼저 들어간 감자칩을 맨 마지막에 먹는것과 같다고 생각했다.



스택의 ADT는 아래의 헤더파일을 본 후 설명하겠다.

```{.cpp}
#define STACK_LEN 100

typedef struct _stack {
	int stackArr[STACK_LEN];
	int topIdx;
}Stack;

void StackInit(Stack * stack);
int IsEmpty(Stack * stack);

void Push(Stack * stack, int data);
int Pop(Stack * stack);
```

1. 스택의 인덱스와 배열 공간을 구조체로 선언
2. StackInit 으로 초기화
3. IsEmpty 로  비어있으면 true, 아니면 false 값을 리턴
4. Push 로 데이터 삽입
5. Pop 으로 topIdx를 줄여 데이터 삭제하고 삭제한 값 리턴


위의 ADT를 함수화 시켜 아래와 같이 코드로 나타냈다.

```{.cpp}
#include <stdio.h>
#include"ArrayStack.h"

void StackInit(Stack *stack) {
	stack->topIdx = -1;
}

int IsEmpty(Stack *stack) {
	if (stack->topIdx == -1)
		return true;
	else
		return false;
}

void Push(Stack * stack, int data) {
	stack->topIdx++;
	stack->stackArr[stack->topIdx] = data;
}

int Pop(Stack * stack) {
	int tmp;
	if (IsEmpty(stack)) {
		printf("텅 비어있음\n");
	}
	else {
		tmp = stack->stackArr[stack->topIdx];
		stack->topIdx--;
		return tmp;
	}
}
```

메인함수를 아래와 같이 나타냈다.

```{.cpp}
#include <stdio.h>
#include "ArrayStack.h"

int main() {
	Stack stack;
	StackInit(&stack);

	Push(&stack, 1);
	Push(&stack, 2);
	Push(&stack, 3);
	Push(&stack, 4);

	while (!IsEmpty(&stack))
		printf("%d ", Pop(&stack));

}
```
