---
layout: single
title: Day 53 HeapSort
---

힙 정렬은 최대 힙으로 만든 후 루트 노드의 값과 맨 끝 노드의 값을 교환해 주는 것을 반복하여 정렬하는 알고리즘이다.


배열 {1,3,4,2,5} 가 있을 때 1회 시행 시
1) 배열을 최대 힙으로 heapify 해주면 {5,4,3,1,2} 가 된다.
2) 루트 노드의 5와 맨 끝 노드 2를 교환해 준다.
3) {2,4,3,1,5} 로 5는 정렬이 완료가 되고 {2,4,3,1}을 가지고 다시 반복해 준다.


코드는 아래와 같다.

```{.cpp}
#include <stdio.h>
#include <stdlib.h>


void Heapify(int heap[], int size) {
	for (int i = 1; i < size;i++) {
		int child = i;
		while (child != 0) {
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

void HeapSort(int arr[], int size) {
	int tmp;
	for (int i = size - 1; i >= 0; i--) {
		Heapify(arr, i + 1);
		tmp = arr[0];
		arr[0] = arr[i];
		arr[i] = tmp;
	}
}

int main() {
	int arr[] = { 1,3,4,2,5 };
	HeapSort(arr, 5);


	for (int i = 0; i < 5;i++) {
		printf("%d ", arr[i]);
	}
}
```

시간 복잡도는 O(n log n) 이다.
