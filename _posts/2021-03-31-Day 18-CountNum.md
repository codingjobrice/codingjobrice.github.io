---
layout: single
title: Day 18 CountNum
---

정수 N을 입력하면 00시 00분 00초 부터 N시 59분 59초 까지 시각중 3이 하나라도 포함되는 경우의 수를 구하는 알고리즘이다.

"이것이 코딩 테스트다 by 나동빈" 을 참고하였다.

```{.cpp}
#include <stdio.h>
#include <string.h>

int check(int a, int b, int c) {
	if (a % 10 == 3 || b / 10 == 3 || b % 10 == 3 || c / 10 == 3 || c % 10 == 3) {
		return true;
	}
	else {
		return false;
	}
}

int main() {
	int n;
	char time[7];
	char* ptr;
	int count = 0;
	scanf_s("%d", &n);
	
	for (int i = 0; i <= n;i++) {
		for (int j = 0; j < 60; j++) {
			for (int k = 0; k < 60; k++) {
				if (check(i, j, k))
					count++;
			}
		}
	}
	
	printf("%d", count);

}
```
