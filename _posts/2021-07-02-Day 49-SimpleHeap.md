---
layout: single
title: Day 49 SimpleHeap
---

힙에 대한 구현이다.


SimpleHeap.h
```{.cpp}
#define HEAP_LEN 100

typedef char HData;
typedef int Priority;

typedef struct _heapElem {
	Priority pr;
	HData data;
}HeapElem;

typedef struct _heap {
	int numOfData;
	HeapElem heapArr[HEAP_LEN];
}Heap;

void HeapInit(Heap* ph);
int HIsEmpty(Heap* ph);

void HInsert(Heap* ph, HData data, Priority pr);
HData HDelete(Heap* ph);
```

SimpleHeap.cpp
```{.cpp}
#include <stdio.h>
#include "SimpleHeap.h"

void HeapInit(Heap* ph) {
	ph->numOfData = 0;
}

int HIsEmpty(Heap* ph) {
	if (ph->numOfData == 0)
		return true;
	else
		return false;
}

int GetParentIDX(int idx) {
	return idx / 2;
}

int GetLChildIDX(int idx) {
	return idx * 2;
}

int GetRChildIDX(int idx) {
	return GetLChildIDX(idx)+ 1;
}

int GetHiPriChildIDX(Heap* ph, int idx) {
	if (GetLChildIDX(idx) > ph->numOfData)  //자식 노드가 없다면
		return 0;

	else if (GetLChildIDX(idx) == ph->numOfData)  //왼쪽 자식 노드 하나만 존재하는 경우
		return GetLChildIDX(idx);

	else {    //자식 노드가 두개인 경우
		if (ph->heapArr[GetLChildIDX(idx)].pr > ph->heapArr[GetRChildIDX(idx)].pr) //오른쪽 자식노드의 우선순위가 크다면
			return GetRChildIDX(idx);

		else //왼쪽 자식노드의 우선순위가 높다면
			return GetLChildIDX(idx);
	}

}

void HInsert(Heap* ph, HData data, Priority pr) {
	int idx = ph->numOfData + 1;
	HeapElem nelem = { pr,data };

	while (idx != 1) {
		if (pr < (ph->heapArr[GetParentIDX(idx)].pr)) {
			ph->heapArr[idx] = ph->heapArr[GetParentIDX(idx)];
			idx = GetParentIDX(idx);
		}
		else
			break;
	}
	ph->heapArr[idx] = nelem;
	ph->numOfData += 1;
}

HData HDelete(Heap* ph) {
	HData retData = (ph->heapArr[1]).data;
	HeapElem lastElem = ph->heapArr[ph->numOfData];

	int parentIdx = 1;
	int childIdx;

	while (childIdx = GetHiPriChildIDX(ph, parentIdx)) {
		if (lastElem.pr <= ph->heapArr[childIdx].pr)
			break; 

		ph->heapArr[parentIdx] = ph->heapArr[childIdx];
		parentIdx = childIdx;
	}

	ph->heapArr[parentIdx] = lastElem;
	ph->numOfData -= 1;
	return retData;
}
```

SimpleHeapMain.cpp
```{.cpp}
#include <stdio.h>
#include "SimpleHeap.h"

int main() {
	Heap heap;
	HeapInit(&heap);

	HInsert(&heap, 'A', 1);
	HInsert(&heap, 'B', 2);
	HInsert(&heap, 'C', 3);
	printf("%c \n", HDelete(&heap));

	HInsert(&heap, 'A', 1);
	HInsert(&heap, 'B', 2);
	HInsert(&heap, 'C', 3);
	printf("%c \n", HDelete(&heap));

	while (!HIsEmpty(&heap))
		printf("%c \n", HDelete(&heap));

}
```


