---
layout: single
title: Day 18 sprintf_s
---

sprintf_s 는 정수를 문자열로 변환해준다.


sprintf_s(buffer,sizeof(buffer),format,가변 인자 리스트) 와 같이 사용하며 예제를 보여주겠다.

```{.cpp}
#include <stdio.h>

int main() {
	char dog[20];
	int num = 109;
	sprintf_s(dog, 20, "%d", num);
	printf("%s", dog);
}
```

위와 같이 dog 라는 문자열에 109 라는 정수를 문자열로 변환해 "%s"로 출력이 가능하다.
