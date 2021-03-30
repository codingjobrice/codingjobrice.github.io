---
layout: single
title: Day 17 SimpleHashTable
---

간단한 해쉬테이블 구현입니다.

```{.cpp}
typedef struct _Info {
	int schnum;
	int age;
}Info;

int Hash(int num) {
	return num % 100;
}

int main() {
	Info arr[100];

	Info ahn = { 20173333,24 };
	arr[Hash(ahn.schnum)] = ahn;
	Info r1 = arr[Hash(20173333)];
}
```
