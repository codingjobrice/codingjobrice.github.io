---
layout: single
title: "Day-3"
---

오늘은 버블정렬입니다. 버블정렬은 각 수의 앞 뒤를 비교하며 자리를 바꿔주며 정렬해주는 방식입니다. 
아래는 오름차순으로 배열을 정렬하는 코드입니다.

```{.cpp}
#include <stdio.h>

void BubbleSort(int arr[], int n) {
	for (int k = 0; k < n-1; k++) {
		for (int i = 0; i < n-k-1; i++) {
			if (arr[i + 1] < arr[i]) {
				int tmp = arr[i];
				arr[i] = arr[i + 1];
				arr[i + 1] = tmp;
			}
		}
	}
}

int main() {
	int arr[] = { 5,3,2,4,1 };
	BubbleSort(arr,5);
	for (int i = 0; i < 5; i++) {
		printf("%d ", arr[i]);
	}

}
```
