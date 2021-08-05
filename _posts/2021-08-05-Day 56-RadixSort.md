---
layout: single
title: Day 56 RadixSort
---

기수 정렬은 다른 정렬과 달리 정렬 순서상 앞서고 뒤섬의 판단을 위한 비교연산이 아니다. 큐의 버켓에 넣고 꺼냄으로서 정렬을 한다.


기수 정렬에는 두 가지 방식은
1) LSD: 작은 자리수 부터 정렬
2) MSD: 큰 자리수 부터 정렬

아래는 코드이다.
```{.cpp}
#include <iostream>
#include <queue>

using namespace std;

void RadixSort(int arr[], int num, int maxLen) {
	queue<int> buckets[10];
	int bi, pos, di, radix;
	int divfac = 1;

	for (pos = 0; pos < maxLen; pos++) {
		for (di = 0; di < num; di++) {
			radix = (arr[di] / divfac) % 10;
			buckets[radix].push(arr[di]);
		}
		for (bi = 0, di = 0; bi < 10; bi++) {
			while (!buckets[bi].empty()) {
				arr[di++] = buckets[bi].front();
				buckets[bi].pop();
			}
		}
		divfac *= 10;
	}
}

int main() {
	int arr[] = { 12,354,8,432 };

	RadixSort(arr, 4, 3);

	for (int i = 0; i < 4; i++) {
		printf("%d ", arr[i]);
	}
}
```

시간복잡도는 O(n) 
