---
layout: single
title: Day 6 UntilOne
---

빼기 또는 나누기로 1이 될 때 까지 연산 횟수를 최소로 하는 알고리즘을 소개하겠다.
어떤 수 n, 나눠질 수를 k라고 하고 n이 k로 나누어 떨어질 때만 나누기 연산이 가능하고 나머진 빼기 연산을 한다.

```{.cpp}
#include <stdio.h>

int main() {
	int n = 20;
	int count = 0;
	int k = 3;

	while (n != 1) {
		if (n % k == 0) {
			n = n / k;
		}
		else {
			n = n - 1;
		}
		count++;
	}

	printf("%d ", count);
}
```
