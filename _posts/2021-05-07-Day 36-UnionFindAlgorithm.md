---
layout: single
title: Day 36 UnionFindAlgorithm
---

Union-Find 알고리즘은 서로소 집합 알고리즘 이라고도 하며 서로소 부분 집합들로 나누어진 원소들의 데이터를 처리하기 위한 자료구조이다.

(서로소는 공통원소가 없는 두 집합을 의미)

findParent 함수로 부모 노드를 반환시키고 unionParent 함수로 a,b(a<b) a를 b의 부모로 설정해준다.

```{.cpp}
#include<stdio.h>

int v, e; //v 노드, e 간선
int parent[100];

int findParent(int a) {
	if (a == parent[a])
		return a;
	return findParent(parent[a]);
}

void unionParent(int a,int b) {
	a = findParent(a);
	b = findParent(b);
	if (a < b)
		parent[b] = a;
	else
		parent[a] = b;
}

int main() {
	printf("노드 입력: ");
	scanf_s("%d", &v);
	printf("간선 입력: ");
	scanf_s("%d", &e);

	for (int i = 1; i <= v; i++) {
		parent[i] = i;
	}

	for (int i = 0; i < e; i++) {
		int a, b;
		printf("두개 노드 입력: \n");
		scanf_s("%d", &a);
		scanf_s("%d", &b);
		unionParent(a, b);
	}

	printf("각 원소가 속한 집합: ");
	for (int i = 1; i <= v; i++) {
		printf("%d ", findParent(i));
	}
	printf("\n");

	printf("부모 테이블: ");
	for (int i = 1; i <= v; i++) {
		printf("%d ", parent[i]);
	}

}
```

소스코드는 "이것이 코딩 테스트다"를 참고하였다.

위의 코드의 시간 복잡도는 O(VM) 이다.
