---
layout: single
title: Day 28 CallByReference,Value
---

call by value 와 call by reference의 차이를 보여주는 예시이다.

```{.cpp}
#include <stdio.h>

void Value(int n1, int n2) {
	int tmp = n1;
	n1 = n2;
	n2 = tmp;
}

void Reference(int* n1, int* n2) {
	int tmp = *n1;
	*n1 = *n2;
	*n2 = tmp;
}

int main() {
	int n1 = 1;
	int n2 = 2;
	printf("원래 값: n1 = %d n2 = %d\n",n1,n2);

	Value(n1, n2);
	printf("CallByValue: n1 = %d n2 = %d\n",n1,n2);

	Reference(&n1, &n2);
	printf("CallByReference: n1 = %d n2 = %d\n",n1,n2);

}
```
