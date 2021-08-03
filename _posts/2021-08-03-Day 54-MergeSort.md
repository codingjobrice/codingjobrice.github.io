---
layout: single
title: Day 54 MergeSort
---

병합 정렬의 기본 원리는 8개 보단 4개가 정렬하기 쉽고 4개 보단 2개가 정렬하기 쉽다는 원리이다. 

8개의 데이터가 있다면 하나의 데이터가 남도록 분할을 하고 결합하는 과정에서 우선 순위를 고려하며 결합한다.


배열 {3,2,4,1,7,6,8,5} 가 있을 때 1회 시행 시

1) 3 / 2 / 4 / 1 / 7 / 6 / 8 / 5 가 모두 하나씩 분할되고
2) 2개씩 결합 시 우선 순위를 고려하여 2 3 / 1 4 / 1 7 / 5 8 로 결합 된다.

위 과정을 재귀적으로 계속 결합하면서 정렬해 주면 {1,2,3,4,5,6,7,8} 로 정렬이 완료가 된다.


아래는 소스코드이다.
```{.cpp}
#include <stdio.h>
#include <stdlib.h>

void MergeTwoArea(int arr[], int left,int mid,int right) {
	int fIdx = left;
	int rIdx = mid + 1;

	int* sortArr = (int*)malloc(sizeof(int) * (right + 1));
	int sIdx = left;

	while (fIdx <= mid && rIdx <= right) {
		if (arr[fIdx] <= arr[rIdx]) {
			sortArr[sIdx] = arr[fIdx++];
		}
		else {
			sortArr[sIdx] = arr[rIdx++];
		}
		sIdx++;
	}

	if (fIdx > mid) {
		for (int i = rIdx; i <= right; i++, sIdx++) {
			sortArr[sIdx] = arr[i];
		}
	}
	else {
		for (int i = fIdx; i <= mid; i++, sIdx++) {
			sortArr[sIdx] = arr[i];
		}
	}

	for (int i = left; i <= right; i++) {
		arr[i] = sortArr[i];
	}
	free(sortArr);
}

void MergeSort(int arr[], int left, int right) {
	int mid;

	if (left < right) {
		mid = (left + right) / 2;

		MergeSort(arr, left, mid);
		MergeSort(arr, mid + 1, right);

		MergeTwoArea(arr, left, mid, right);
	}
}

int main() {
	int arr[] = { 3,2,4,1,7,6,8,5 };

	MergeSort(arr, 0, 7);

	for (int i = 0; i < 8;i++) {
		printf("%d ", arr[i]);
	}
}
```
