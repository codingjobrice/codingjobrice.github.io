---
layout: single
title: Day 55 QuickSort
---

퀵 정렬은 코드로 설명하겠다.

```{.cpp}
#include <stdio.h>

void Swap(int arr[], int a, int b) { //값의 교환을 실행해주는 함수
	int tmp = arr[a];
	arr[a] = arr[b];
	arr[b] = tmp;
}

int Partition(int arr[],int left, int right) { //1회 시행을 하는 함수이고 이를 가지고 QuickSort 함수에서 재귀적으로 정렬을 완료해준다.
	int low = left + 1; //{3,5,1,2,4}가 있다면 5에 해당
	int high = right; // 4

	int pivot = arr[left]; //피벗으로 기준을 잡아준다.

	while (low <= high) {
		while (pivot>=arr[low] && low<=right) { //피벗보다 작은 값이면 low를 증가
			low++;
		}

		while (pivot <= arr[high] && high >= left + 1) { //피벗보다 큰 값이면 high를 감소
			high--;
		}
		if (low <= high) { //위의 증가와 감소가 완료되는 시점에 그 값들을 교환해준다.
			Swap(arr, low, high);
		}
	}

	Swap(arr, left, high); //위의 이중 while문의 연산이 끝났을 때 arr[high] 와 arr[left]의 값을 교환해 주면 1회 시행이 완료가 된다.

	return high;
}

void QuickSort(int arr[],int left,int right) { //Partition으로 1회 시행을 했다면 다시 high 인덱스에서 좌,우로 재귀적으로 정렬 해주면 된다.
	if (left <= right) {
		int pivot = Partition(arr, left, right);
		QuickSort(arr, left, pivot - 1);
		QuickSort(arr, pivot + 1, right);
	}
}

int main() {
	int arr[] = { 3,5,1,2,4 };

	QuickSort(arr, 0, 4);

	for (int i = 0; i < 5; i++) {
		printf("%d ", arr[i]);
	}
}
```

최선의 경우에 시간복잡도는 O(n log n) 이고 이미 정렬이 완료가 된 배열에서 퀵 정렬을 실행하면 최악의 경우가 되는데 이 때 시간복잡도는 O(n^2) 이 된다.
