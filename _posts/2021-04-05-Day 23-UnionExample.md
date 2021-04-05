---
layout: single
title: Day 23 UnionExample
---

공용체(Union)는 하나의 메모리를 서로 다른 변수가 공유하며 사용하는 것을 말한다.

```{.cpp}
#include <stdio.h>

union student {
	int tot;
	char grade;
};

int main() {
	union student u;
	
	u.tot = 300;
	u.grade = 'A';

	printf("총점: %d\n",u.tot);
	printf("등급: %c\n", u.grade);
}
```

위와 같이 공용체를 써보았는데 총점의 숫자가 321로 오류가 생긴다. 위는 tot와 grade가 메모리를 공유하면서 등급 A가 총점 300에 영향을 줬기 때문이다.


위와 같은 오류를 없애기 위해서는 하나 선언 후 사용해 줘야한다.

```{.cpp}
#include <stdio.h>

union student {
	int tot;
	char grade;
};

int main() {
	union student u;
	
	u.tot = 300;
	printf("총점: %d\n", u.tot);  // 
	u.grade = 'A';
	printf("등급: %c\n", u.grade);
}
```
