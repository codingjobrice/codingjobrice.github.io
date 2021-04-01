---
layout: single
title: Day 19 DataStructure ListAddress
---

Fundamentals of Data Structure in C 책의 57p 배열을 선언하고 그 주솟값을 출력하는 코드이다.

```{.cpp}
#include <stdio.h>

void printA(int *ptr,int rows) {
	for (int i = 0; i < rows; i++) {
		printf("%d %d\n",ptr+i,*(ptr+i));
	}
}

int main() {
	int arr[] = { 0,1,2,3,4 };
	printA(arr,5);
}
```
