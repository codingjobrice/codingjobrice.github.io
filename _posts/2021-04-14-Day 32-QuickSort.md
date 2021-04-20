---
layout: single
title: Day 32 QuickSort
---

퀵 정렬은 기준 데이터(pivot)을 설정하고 그 값보다 작고 큰 데이터의 위치를 바꿔가는 것을 반복하는 정렬 방식이다. 

Partition 후에 재귀적으로 QuickSort 하는 방식으로 코드를 작성했다.



```{.cpp}
#include <stdio.h>

void Swap(int arr[],int a,int b) { //값의 교환을 위한 Swap 함수이다.
	int tmp = arr[a];
	arr[a] = arr[b];
	arr[b] = tmp;
}

int Partition(int arr[],int left, int right) {  //arr[high] 와 pivot의 위치를 바꿔서 pivot의 위치를 찾아준다.
	int pivot = arr[left];
	int low = left + 1;
	int high = right;

	while (low<=high) {
		while (pivot >= arr[low] && low<=right) { //&& 뒤의 조건은 같은 수가 있는 존재하는 경우를 대비한 조건이다.
			low++;
		}
		while (pivot <= arr[high]&& high>=left+1) {
			high--;
		}
		if (low <= high) {
			Swap(arr, low, high);
		}
	}
	Swap(arr, left, high);
	return high;
}

void Quicksort(int arr[],int left, int right) {
	if (left <= right) {
		int pivot = Partition(arr, left, right);
		Quicksort(arr,left,pivot-1);		//한번 정렬 후 pivot을 기준으로 오른쪽 왼쪽 다시 재귀적으로 Partition 해준다.
		Quicksort(arr, pivot + 1, right);		
	}
}

int main() {
	int arr[] = { 3,5,7,1,8,2,6 };
	Quicksort(arr,0,6);
	for (int i = 0; i < 7; i++) {
		printf("%d ", arr[i]);
	}
}
```

시간 복잡도는 nlogn 으로 삽입, 선택보다 효율적인 알고리즘이다. 하지만 이미 정렬되어 있는 경우의 정렬 과정에서는 O(n^2)의 시간 복잡도를 가지게 되는 점 유의하자.
