---
layout: single
title: Day 46 BinaryTree
---

트리는 계층적 관계를 표현하는 구조로 집안 족보나 기업의 조직도로 사용된다.

노드, 간선, 루트 노드, 단말 노드(리프 노드), 내부 노드(비단말 노드) 로 구성되며 각각의 설명은 생략하겠다.


트리의 종류 중 하나인 이진 트리를 구현하겠다.

이진트리는 루트 노드를 중심으로 두 개의 서브 트리로 나뉘어지고 나뉘어진 두 서브트리가 모두 이진트리인 트리를 재귀적으로 정의한다.


BinaryTree.h
```{.cpp}
typedef struct _bTreeNode {
	int data;
	struct _bTreeNode* left;
	struct _bTreeNode* right;
}BTreeNode;

BTreeNode* MakeBTreeNode(void);
int GetData(BTreeNode* bt);
void SetData(BTreeNode* bt, int data);

BTreeNode* GetLeftSubTree(BTreeNode* bt);
BTreeNode* GetRightSubTree(BTreeNode* bt);

void MakeLeftSubTree(BTreeNode* main, BTreeNode* sub);
void MakeRightSubTree(BTreeNode* main, BTreeNode* sub);
```

BinaryTree.cpp
```{.cpp}
#include <stdio.h>
#include <stdlib.h>
#include "BinaryTree.h"

BTreeNode* MakeBTreeNode(void) {
	BTreeNode* nd = (BTreeNode*)malloc(sizeof(BTreeNode));
	nd->left = NULL;
	nd->right = NULL;
	return nd;
}

int GetData(BTreeNode* bt) {
	return bt->data;
}
void SetData(BTreeNode* bt, int data) {
	bt->data = data;
}

BTreeNode* GetLeftSubTree(BTreeNode* bt) {
	return bt->left;
}

BTreeNode* GetRightSubTree(BTreeNode* bt) {
	return bt->right;
}

void MakeLeftSubTree(BTreeNode* main, BTreeNode* sub) {
	if (main->left != NULL)
		free(main->left);

	main->left = sub;
}

void MakeRightSubTree(BTreeNode* main, BTreeNode* sub) {
	if (main->right != NULL)
		free(main->right);

	main->right = sub;
}
```


BinaryTreeMain.cpp
```{.cpp}
#include <stdio.h>
#include "BinaryTree.h"

int main() {
	BTreeNode* bt1 = MakeBTreeNode();
	BTreeNode* bt2 = MakeBTreeNode();
	BTreeNode* bt3 = MakeBTreeNode();
	BTreeNode* bt4 = MakeBTreeNode();

	SetData(bt1, 1);
	SetData(bt2, 2);
	SetData(bt3, 3);
	SetData(bt4, 4);

	MakeLeftSubTree(bt1, bt2);
	MakeRightSubTree(bt1, bt3);
	MakeLeftSubTree(bt2, bt4);

	printf("%d \n",GetData(GetLeftSubTree(bt1)));
	printf("%d \n", GetData(GetLeftSubTree(GetLeftSubTree(bt1))));
}
```
