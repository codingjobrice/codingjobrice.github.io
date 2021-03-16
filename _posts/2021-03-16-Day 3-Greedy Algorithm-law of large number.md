---
layout: sigle
title: Day-3
---

그리디 알고리즘의 예시 중 큰 수의 법칙을 코드화 시켜보았다. 
큰 수의 법칙은 배열이 존재하고 주어진 수들을 k번 초과해 더해질 수 없는 조건으로 m번 더해 가장 큰 수를 만드는 법칙이다.
수식으로 하나 반복문으로 하나 작성해보았다. 이전의 버블정렬을 사용했다.

1 수식


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
	int arr[] = { 5,2,3,1,4 };
	int n = sizeof(arr)/sizeof(int);
	int m = 5; //m번 더한다.
	int k = 3; //k번 초과할 수 없다.
	BubbleSort(arr,n);

	int first = arr[n-1];
	int second = arr[n - 2];

	int result = first * k * (m / (k + 1)) + first * (m % (k + 1)) + second*(m / (k + 1));

	printf("%d ", result);
}
```


2 반복문


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
	int arr[] = { 5,2,3,1,4 };
	int n = sizeof(arr)/sizeof(int);
	int m = 5;
	int k = 3;
	int result = 0;
	BubbleSort(arr,n);

	int first = arr[n-1];
	int second = arr[n - 2];

	while (1) {
		for (int i = 0; i < k; i++) {
			if (m == 0)
				break;
			result += first;
			m--;
		}
		if (m == 0) {
			break;
		}
		result += second;
		m--;
	}
	printf("%d", result);
}
```
