---
layout: single
title: Day 7 Factorial
---

!(팩토리얼)은 예로 들면 5! = 5x4x3x2x1 = 120 와 같이 연산하는 부호다.
이를 재귀적으로 구현해보았다.

```{.cpp}
#include <stdio.h>

int Factorial(int n) {
	if (n == 1)
		return 1;
	else
		return n*Factorial(n - 1);
}

int main() {
	printf("%d ", Factorial(5));
}
```
