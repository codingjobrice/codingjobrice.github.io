---
layout: single
title: Day 34 Dynamic Programming
---

다이나믹 프로그래밍은 메모리 공간을 약간 더 사용하면 연산 속도를 비약적으로 증가시킬 수 있는 방법으로 동적 계획법 이라고도 한다.


다이나믹 프로그래밍을 사용하기 위해서는 두 가지의 조건을 만족해야 된다.

1. 큰 문제를 작은 문제로 나눌 수 있다.(최적 부분 구조)

2. 작은 문제에서 구한 정답은 그것을 포함하는 큰 문제에서도 동일하다.(중복되는 부분 문제)


다이나믹 프로그래밍 중 한 기법인 메모이제이션으로 예제를 설명하겠다.

메모이제이션은 한 번 구한 결과를 메모리 공간에 메모해두고 같은 식을 다시 호출하면 메모한 결과를 그대로 가져오는 기법으로 탑다운 방식로 캐싱이라고도 한다.

피보나치 수열로 예를 들겠다.

```{.cpp}
#include <stdio.h>

int fibo(int n) {
	if (n == 1)
		return 1;
	else if (n == 2)
		return 1;
	else
		return fibo(n - 1) + fibo(n - 2);
}

int main() {
	printf("%d ", fibo(4));
}
```

보통 피보나치 수열을 소스코드로 표현하면 위와 같다. 위의 시간 복잡도는 O(2^n) 으로 n이 100만 되도 엄청난 수가 나와 엄청난 시간이 소요된다.

이를 메모이제이션으로 해결하면 아래와 같은 소스코드로 표현 가능하다.

```{.cpp}
#include <stdio.h>

int arr[100] = { 0, };

int fibo(int n) {
	if (n == 1)
		return 1;
	else if (n == 2)
		return 1;
	if (arr[n] != 0)
		return arr[n];

	arr[n] = fibo(n - 1) + fibo(n - 2);
	return arr[n];
}

int main() {
	printf("%d ", fibo(4));
}
```

첫 번째 소스코드와의 차이점을 보자면 arr 이라는 배열이 생겼고 그 배열에 n-1, n-2 번째 값들이 저장되어 있다는 것이다.

이를 통해 불필요한 연산을 줄이고 속도가 증가되며 시간 복잡도는 O(n)이 된다.


다음은 보텀업 방식으로 표현해 보겠다.

보텀업 방식은 단순히 반복문을 이용해 소스코드를 작성하는 경우 작은 문제부터 차근차근 답을 도출하는 방식이다.


```{.cpp}
#include <stdio.h>

int arr[100] = { 0, };

/*int fibo(int n) {
	if (n == 1)
		return 1;
	else if (n == 2)
		return 1;
	if (arr[n] != 0)
		return arr[n];

	arr[n] = fibo(n - 1) + fibo(n - 2);
	return arr[n];
}*/

int main() {
	arr[1] = 1;
	arr[2] = 1;

	for (int i = 3; i <=4;i++) {
		arr[i] = arr[i - 1] + arr[i - 2];
	}

	printf("%d", arr[4]);
}
```
