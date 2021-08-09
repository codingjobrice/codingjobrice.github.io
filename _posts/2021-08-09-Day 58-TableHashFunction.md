---
layout: single
title: Day 58 TableHashFunction
---

테이블은 사전과 같은 자료구조로 데이터가 키와 값이 하나의 쌍을 이루는 자료구조이다.

아래는 테이블의 예시를 코드로 나타냈다.

```{.cpp}
#include <stdio.h>

typedef struct _empInfo {
	int num;
	int age;
}Info;

int GetHashValue(int num) {
	return num % 100;
}

int main() {
	Info infoArr[100];

	Info emp1={ 20175209,24 };
	Info emp2 = { 20175555,24 };
	Info emp3 = { 20169989,25 };

	Info r1, r2, r3;

	infoArr[GetHashValue(emp1.num)] = emp1;
	infoArr[GetHashValue(emp2.num)] = emp2;
	infoArr[GetHashValue(emp3.num)] = emp3;

	r1 = infoArr[GetHashValue(20175209)];
	r2 = infoArr[GetHashValue(20175555)];
	r3 = infoArr[GetHashValue(20169989)];

	printf("번호: %d, 나이: %d \n",r1.num,r1.age);
	printf("번호: %d, 나이: %d \n", r2.num, r2.age);
	printf("번호: %d, 나이: %d \n", r3.num, r3.age);
}
```

위와 같이 키 값을 번호로 정하고 그에 대응하는 값을 나이로 설정한 코드이다.


저장 과정에서 번호의 길이가 너무 길어 두 자리 숫자를 바꿔주는 함수를 사용하였고 이 함수도 해쉬 함수의 일종이라고 볼 수 있다.

해쉬 함수는 키 값의 범위를 줄여주기도 하고 아예 다른 숫자로 바꾸는 역할도 한다.

