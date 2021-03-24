---
layout: single
title: Day 11 SelectionSort
---

선택정렬 알고리즘 입니다.

```{.cpp}
#include <stdio.h>

void SelectionSort(int arr[],int n) {
	int i, j;
	int maxIdx;
	int temp;

	for (i = 0; i < n - 1;i++) {
		maxIdx = i;
		for (j = i + 1; j < n; j++) {
			if (arr[j] < arr[maxIdx])
				maxIdx = j;
		}
		temp = arr[i];
		arr[i] = arr[maxIdx];
		arr[maxIdx] = temp;
	}
}
int main() {
	int arr[4] = { 3,4,2,1 };

	SelectionSort(arr, 4);

	for (int i = 0; i < 4; i++) {
		printf("%d ", arr[i]);
	}
}
```
