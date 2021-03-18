---
layout: single
title: Day 6 Fibonacci Sequence
---

재귀적 용법 중 대표적인 예시인 피보나치 수열에 대해 코딩해보았다.
피보나치 수열은 첫째 항 0, 두번째 항 1 으로 시작해 세번째 항은 앞의 두 항을 더해 만들어 가는 수열이다.

```{.cpp}
#include <stdio.h>

int Fibo(int n) {
	if (n == 1) {
		return 0;
	}
	else if (n == 2) {
		return 1;
	}
	else {
		return Fibo(n - 1) + Fibo(n - 2);
	}
}

int main() {
	for (int i = 1; i < 10; i++) {
		printf("%d ", Fibo(i));
	}
}
```
