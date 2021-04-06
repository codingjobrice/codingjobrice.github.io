---
layout: single
title: Day 24 ReverseChar
---

문자열을 거꾸로 출력하는 알고리즘입니다.

```{.cpp}
#include <stdio.h>
#include <string.h>
#include <malloc.h>

int main() {
	int size;

	char word[100];

	scanf_s("%s", word, 100);

	int count = strlen(word);

	char* p = word;

	for (int i = 0; i < count; i++) {
		printf("%c", *(p + count - (i + 1)));
	}
}
```
