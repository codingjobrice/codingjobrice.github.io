---
layout: single
title: Day 16 InterpolationSearch
---

보간탐색 알고리즘이다.

```{.cpp}
#include <stdio.h>

int InterpolSearch(int arr[],int first,int last,int target) {
	int mid;

	if (first > last)
		return -1;

	mid = ((double)(target - arr[first]) / (arr[last] - arr[first]) * (last - first)) + first;

	if (arr[mid] == target)
		return mid;
	else if (target < arr[mid])
		return InterpolSearch(arr, first, mid - 1, target);
	else
		return InterpolSearch(arr, mid + 1, last, target);
}

int main() {
	int arr[] = { 1,3,5,7,9 };

	int idx = InterpolSearch(arr, 0, 4, 5);

	printf("%d ", idx);

}
```
