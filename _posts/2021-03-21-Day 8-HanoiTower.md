---
layout: single
title: Day 8 HanoiTower
---

이번 알고리즘은 하노이 타워이다.
그림으로 설명하는 것이 편하나 아직 그림을 그려서 올릴 줄 모르기 때문에 생략한다.

```{.cpp}
#include <stdio.h>

void Hanoi(int n, char from, char by, char to) {
	if (n == 1)
		printf("%d 번째 원반 %c에서 %c로 이동\n",n,from,to);
	else {
		Hanoi(n - 1, from, to, by);
		printf("%d 번째 원반 %c에서 %c로 이동\n", n, from, to);
		Hanoi(n - 1, by, from, to);
	}
}

int main() {
	Hanoi(3, 'A', 'B', 'C');
}
```
