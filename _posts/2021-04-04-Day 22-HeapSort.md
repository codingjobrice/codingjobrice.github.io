---
layout: single
title: Day 22 HeapSort
---

힙정렬 구현입니다.

```{.cpp}
#include <stdio.h>
#include <stdlib.h>


void Heapify(int heap[],int size) {
	for (int i = 1; i < size;i++) {
		int child = i;
		while(child !=0) {
			int root = (child - 1) / 2;
			if (heap[root] < heap[child]) {
				int tmp = heap[root];
				heap[root] = heap[child];
				heap[child] = tmp;
			}
			child = root;
		} 
	}
}

void HeapSort(int arr[],int size) {
	int tmp;
	for (int i = size -1; i >= 0; i--) {
		Heapify(arr, i+1);
		tmp = arr[0];
		arr[0] = arr[i];
		arr[i] = tmp;
	}
}

int main() {
	int arr[] = {1,3,4,2,5};
	HeapSort(arr, 5);
	

	for (int i = 0; i < 5;i++) {
		printf("%d ", arr[i]);
	}
}
```
