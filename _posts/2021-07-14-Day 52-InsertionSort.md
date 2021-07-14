---
layout: single
title: Day 52 InsertionSort
---

삽입 정렬은 정렬된 부분과 그렇지 않은 부분 두 가지로 나누어 정렬 안 된 부분에 있는 데이터를 정렬 된 부분의 특정 위치에 삽입하는 정렬 방식이다.


배열 {4,3,1,2} 가 있을 때 
1) 1회 시행 시 4는 정렬됬다고 보고 3,1,2 를 정렬되지 않은 것으로 보고 3을 정렬된 부분의 자신의 위치에 정렬시켜 {3,4,1,2}가 된다.
2) 2회 시행 시 3,4 를 정렬된 부분, 1,2를 정렬되지 않은 부분으로 보고 1을 마찬가지로 정렬시켜 {1,3,4,2}가 된다.
3) 마찬가지 2를 적용시켜 {1,2,3,4}로 정렬이 된다.


코드는 아래와 같다.
```{.cpp}
#include<stdio.h>

void InsertionSort(int arr[],int n) {
	int k;
	for (int i = 1; i < n; i++) {
		int data = arr[i];
		for (k = i - 1; k >= 0; k--) {
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
	int arr[] = { 4,3,1,2 };

	InsertionSort(arr, 4);

	for (int i = 0; i < 4; i++) {
		printf("%d ", arr[i]);
	}
}
```

시간복잡도는 버블 정렬, 선택 정렬과 같이 O(n^2) 이다.
