---
layout: single
title: Day 21 FilePointerExampleNeedToBeModified
---

1 30 30 30 30 30 
2 30 20 10 10 10

예를 들어 위와 같이 점수가 test 라는 텍스트 파일에 저장되어 있을 때 30점 초과이면 pass.txt 30점 이하이면 fail.txt에 저장하게 하는 코드이다.

```{.cpp}
#include <stdio.h>

int main() {
	FILE* rfp, * wfp, * wfpf;
	int line, n1, n2, n3, n4, n5;
	int sum = 0;

	fopen_s(&rfp, "test.txt", "r");
	fopen_s(&wfp, "pass.txt", "w");
	fopen_s(&wfpf, "fail.txt", "w");

	while (!feof(rfp)) {
		fscanf_s(rfp, "%d %d %d %d %d %d", &line, &n1, &n2, &n3, &n4, &n5);
		sum = n1 + n2 + n3 + n4 + n5;
		if (sum / 5 > 30) {
			fprintf(wfp, "%d %d %d %d %d %d\n", line, n1, n2, n3, n4, n5);
		}
		else {
			fprintf(wfpf, "%d %d %d %d %d %d\n", line, n1, n2, n3, n4, n5);
		}
		fclose(rfp);
		fclose(wfp);
		fclose(wfpf);
	}
}
```
