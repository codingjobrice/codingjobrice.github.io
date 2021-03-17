---
layout: single
title: Greedy Algorithm - Card Game
---


그리디 알고리즘 중 카드게임을 구현해봤다. 
3 2 1
2 2 1
2 2 2
위와 같이 2차 행렬이 존재할 때 열을 m이라 하고 행을 n 이라고 했을 때 각 행에서 최소값을 찾아 그 최솟값 중 최댓값을 찾는 알고리즘이다.


```{.cpp}
#include <stdio.h>

int main() {
	int m = 3;
	int n = 3;
	int min[3];
	int max;
	int arr[3][3] = { {3,2,1},{2,2,1},{2,2,2} };

	for (int i = 0; i < n; i++) {
		for (int k = 0; k < m - 1; k++) {
			min[i] = arr[i][k];
			if (min[i] > arr[i][k+1]) {
				min[i] = arr[i][k+1];
			}
		}
	}
	max = min[0];
	for (int i = 0; i < n-1;i++) {
		if (max < min[i+1]) {
			max = min[i + 1];
		}
	}

	printf("%d", max);
}
```

코드를 위와 같이 만들었고 배열의 앞 뒤의 크기를 비교해가며 최소, 최댓값을 찾을 수 있었다.
