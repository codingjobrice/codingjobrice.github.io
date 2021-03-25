---
layout: single
title: Day 12 BinarySearch
---

이진탐색은 정렬된 배열에서 숫자를 탐색할 때 반으로 쪼개면서 범위를 좁혀가 찾는 알고리즘이다.

```{.cpp}
#include <stdio.h>

int BinarySearch(int arr[],int left,int right,int search) {
	int mid = (left + right) / 2;

	if (search < arr[mid])
		return BinarySearch(arr, left, mid - 1, search);
	else if (search > arr[mid])
		return BinarySearch(arr, mid + 1, right,search);
	else
		return search;
}

int main() {
	int arr[] = { 1,3,5,7,9 };

	int find = BinarySearch(arr, 0, 4, 3);

	printf("%d ", find);
}
```
