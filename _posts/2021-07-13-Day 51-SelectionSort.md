---
layout: single
title: Day 51 SelectionSort
---

선택정렬은 오름차순으로 정렬할 때 배열에서 최솟값을 찾아 맨 앞에서 부터 정렬해 가는 방식이다.

배열 {4,3,1,2} 가 있을 때 선택정렬 1회 시행 시 1이 최소값이므로 맨 앞의 숫자 4와 교환해 {1,3,4,2}가 된다.


위의 과정을 다시 3,4,2 에 적용하면 된다.


코드는 아래와 같다.

```{.cpp}
#include <stdio.h>

void BubbleSort(int arr[], int n) {

	for (int i = 0; i < n - 1; i++) {
		int maxIdx = i; 
		for (int k = i + 1; k < n; k++) {
			if (arr[k] < arr[maxIdx]) {
				maxIdx = k; //최솟값을 찾는 과정
			}
			
		}
		int tmp = arr[i]; //최솟값과 교환
		arr[i] = arr[maxIdx];
		arr[maxIdx] = tmp;
	}
}

int main() {
	int arr[] = { 4,3,1,2 };
	BubbleSort(arr, sizeof(arr)/sizeof(int));

	for (int i = 0;i < 4; i++) {
		printf("%d ", arr[i]);
	}
}
```

위의 2중 for문 으로 인해 수행 횟수는 (n-1) + (n-2) + ...+ 2 + 1 로 시간복잡도는 O(n^2) 이 된다.
