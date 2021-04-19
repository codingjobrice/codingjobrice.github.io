---
layout: single
title: Day 14 InsertionSort
---

삽입정렬 알고리즘은 데이터를 하나씩 확인하며, 각 데이터를 적절한 위치에 삽입하는 것을 반복하는 정렬 방식이다. 첫번째 데이터는 정렬되어있다고 판단하고 두번째 데이터 부터 삽입해 가면 된다.



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


선택 정렬과 마찬가지로 시간 복잡도는 반복문이 두번 중첩되므로 O(n^2) 이라고 볼 수 있다. 
