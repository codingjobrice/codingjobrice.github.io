---
layout: single
title: day 13 Eclid Algorithm
---

유클리드 알고리즘으로 최대공약수를 찾는다.


```{.cpp}
#include <stdio.h>

int gcd(int a, int b) {
	if (b == 0)
		return a;
	else
		return gcd(b, a % b);
}

int main() {
	printf("%d ",gcd(32,12));
}
```
