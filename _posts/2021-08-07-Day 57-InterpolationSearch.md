---
layout: single
title: Day 57 InterpolationSearch
---

보간 탐색은 이진 탐색이 반씩 쪼개서 탐색을 시행하였다면 탐색 대상이 앞쪽에 위치해 있으면 앞쪽에서 탐색을 시행하는 탐색이다.


기본적인 구현에서는 이진 탐색과 비슷하지만 이진 탐색의 mid 는 배열의 크기/2를 해준 것이라면

보간 탐색은 ((double)(target - arr[first]) / (arr[last] - arr[first]) * (last - first)) + first; 으로 설정하면 된다.

아래는 코드이다.

```{.cpp}
#include <stdio.h>

int ISearch(int arr[], int first,int last,int target) {
	if (arr[first]>target || arr[last]< target)
		return false;

	int mid = ((double)(target - arr[first]) / (arr[last] - arr[first]) * (last - first)) + first;
	
	if (target > arr[mid])
		return ISearch(arr, mid+1, last, target);
	else if (target < arr[mid])
		return ISearch(arr, first, mid-1, target);
	else
		return mid;
}

int main() {
	int arr[] = { 1,3,5,7,9 };
	int idx = ISearch(arr,0,4,7);

	printf("인덱스는 %d ", idx);
}
```
