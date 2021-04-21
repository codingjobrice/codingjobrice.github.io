---
layout: single
title: Day 33 CountSort
---

계수 정렬은 데이터의 크기 법위가 제한되어 정수 형태로 표현 가능할 때 각 데이터가 몇 번 등장했는지 그 횟수를 세서 정렬하는 알고리즘이다.

```{.cpp}
#include <stdio.h>
#define SIZE 7


int main() {
	int arr[] = { 3,4,4,5,1,2,1 };

	int count[SIZE + 1] = { 0, };  //배열 0으로 초기화

	for (int i = 0; i < SIZE; i++) {
		count[arr[i]] += 1;
	}
	for (int i = 0; i < SIZE; i++) {
		for (int k = 0; k < count[i]; k++) {
			printf("%d ", i);
		}
	}
}
```

계수 정렬의 시간 복잡도는 O(n+k) 로 (k는 데이터 중 최대값의 크기) 기수 정렬과 같이 정렬 알고리즘 중 가장 빠르다고 볼 수 있다.
