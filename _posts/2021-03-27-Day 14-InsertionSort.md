---
layout: single
title: Day 14 InsertionSort
---

삽입정렬 알고리즘 입니다.

```{.cpp}
#include <stdio.h>

void Insertion(int arr[],int size) {
	int i, k;
	int data;

	for (i = 1; i < size;i++) {
		data = arr[i];
		for (k = i - 1;k >= 0;k--) {
			if (arr[k] > data) {
				arr[k + 1] = arr[k];
			}
			else {
				break;
			}
		}
		arr[k + 1] = data;
	}
}

int main() {
	int arr[] = { 3,4,2,1 };
	Insertion(arr, 4);
	for (int i = 0; i < 4; i++) {
		printf("%d ", arr[i]);
	}
}
```
