---
layout: single
title: Day 29 AdjacencyMatrix
---

인접행렬의 예시입니다.


```{.cpp}
#include <stdio.h>
#define INF 999999999

int main() {
	int graph[3][3] = {
		{0,7,5},
		{7,0,INF},
		{5,INF,0}
	};

	printf("%d", graph[0][2]);
}
```
