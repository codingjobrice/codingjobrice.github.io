---
layout: single
title: Day 50 BubbleSort
---

버블 정렬은 오름차순으로 정렬할 때 배열의 앞, 뒤를 비교하며 가장 큰 수를 맨 뒤에 저장하는 방식을 반복하여 데이터를 정렬한다.

{4,3,1,2}라는 배열에 버블 정렬 1회 시행을 나타내면


1) 3,4,1,2
2) 3,1,4,2
3) 3,1,2,4


위와 같이 정렬되고 4가 정렬 됬으니 앞의 3,1,2 를 다시 버블정렬을 시행해주면 된다.


코드는 아래와 같다.

```{.cpp}
#include <stdio.h>

void BubbleSort(int arr[], int n) {
	
	for (int i = 0; i < n - 1; i++) {
		for (int k = 0; k < n - 1 - i; k++) {
			if (arr[k] > arr[k + 1]) {
				int tmp = arr[k]; 
				arr[k] = arr[k + 1];
				arr[k + 1] = tmp;  //앞 뒤의 교환이 이루어진다.
			}
		}
	}
}

int main() {
	int arr[] = { 4,3,1,2 };
	BubbleSort(arr, sizeof(arr) / sizeof(int));

	for (int i = 0; i < sizeof(arr) / sizeof(int); i++) {
		printf("%d ", arr[i]);
	}
}
```
