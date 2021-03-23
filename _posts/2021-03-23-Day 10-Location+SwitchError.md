---
layout: single
title: Location + SwitchError
---

가로, 세로 정방행렬의 크기를 n으로 입력 받고 6자리 문자열을 입력 받아 R이면 오른쪽 한칸으로 움직이게 하는 역할을 하며 L,U,D도 각각의 역할을 가진다. 출력값은 6개의 이동 후 좌표이다.


---
이 코드를 작성하면서 switch문에서 약간의 실수가 있었는데 switch문에서 아래 코드와 같이 break를 걸어주지 않으면 1을 걸어 줬을 때 case 1에서 case 2까지 실행이 된다. 


```{.cpp}
#include <stdio.h>

int main() {
	int num = 1;
	
	switch (num) {
	case 1:
		printf("1 입니다.\n");
	case 2:
		printf("2 입니다.\n");
		break;
	case 3:
		printf("3 입니다.\n");
    break;
	}

}
```
case 하나만 실행하기 위해서는 case 2 처럼 break를 꼭 걸어줘야 한다.



아래는 상하좌우 알고리즘이다.

```{.cpp}
#include <stdio.h>

int main() {
	int n;
	char dir[10];
	int a = 1;
	int b = 1;
	int imsi = 1;
	printf("몇칸 할지 입력: ");
	scanf_s("%d", &n);
	printf("RLUD 중 6자리 입력: ");
	scanf_s("%s", dir, 10);
	
	for (int i = 0; i < 6; i++) {
		switch (dir[i]) {
		case 'R':
			if (b < n) {
				printf("R 입니다.\n");
				b++;
			}
			else {
				break;
			}
			break;
		case 'L':
			if (b > 1) {
				printf("L 입니다.\n");
				b--;
			}
			else {
				break;
			}
			break;
		case 'U':
			if (a > 1) {
				printf("U 입니다.\n");
				a--;
			}
			else {
				break;
			}
			break;
		case 'D':
			if (a < n) {
				printf("D 입니다.\n");
				a++;
			}
			else {
				break;
			}
			break;
		}
	}
	printf("%d %d", a, b);
}
```
