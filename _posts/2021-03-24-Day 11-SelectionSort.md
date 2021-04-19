---
layout: single
title: Day 11 SelectionSort
---

선택 정렬 알고리즘은 무작위의 데이터가 있을 때 가장 작은 데이터를 선택해 맨 앞의 데이터와 위치를 바꾸고 
그 다음 작은 데이터를 다시 선택해 그 다음 위치에 있는(두번 째) 데이터와 위치를 바꿔주는 과정을 반복해 정렬하는 알고리즘이다. 


아래는 선택정렬 알고리즘 코드이다.


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

선택 정렬의 시간 복잡도를 계산해 보면 n + n-1 + n-2 ... 2 라 n x n(n+1)/2 로 O(n²) 이다. 간단하게 for 문이 이중으로 쓰여 저런 시간복잡도가 나온다고 이해하자.
