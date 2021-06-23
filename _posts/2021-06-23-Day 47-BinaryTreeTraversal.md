---
layout: single
title: Day 47 BinaryTreeTraversal
---

바로 이전의 트리를 구현한 것에 더하여 트리의 순회에 대해 설명하겠다.

트리의 순회는 세 가지가 있고 각각 중위 순회, 전위 순회, 후위 순회가 있다.


세 순회의 기준을 루트 노드로 잡는다.


1.전위 순회는 루트 노드를 먼저 방문하고 왼쪽 서브 트리, 오른쪽 서브트리 순으로 방문한다.
2.중위 순회는 왼쪽 서브트리, 루트 노드, 오른쪽 서브트리 순으로 방문한다.
3.후위 순회는 왼쪽 서브트리, 오른쪽 서브트리, 루트 노드 순으로 방문한다.


아래는 지난번 트리의 소스코드에 순회를 더한 코드이다.


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

void InorderTraverse(BTreeNode* bt);
void PreorderTraverse(BTreeNode* bt);
void PostorderTraverse(BTreeNode* bt);
```

BinaryTree.pp
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

void InorderTraverse(BTreeNode* bt) {
	if (bt == NULL)
		return;

	InorderTraverse(bt->left);
	printf("%d ", bt->data);
	InorderTraverse(bt->right);
}

void PreorderTraverse(BTreeNode* bt) {
	if (bt == NULL)
		return;
	
	printf("%d ", bt->data);
	PreorderTraverse(bt->left);
	PreorderTraverse(bt->right);
}
void PostorderTraverse(BTreeNode* bt) {
	if (bt == NULL)
		return;

	PostorderTraverse(bt->left);
	PostorderTraverse(bt->right);
	printf("%d ", bt->data);
}
```

BinaryyTreeMain.cpp
```{.cpp}
#include <stdio.h>
#include "BinaryTree.h"

int main() {
	BTreeNode* bt1 = MakeBTreeNode();
	BTreeNode* bt2 = MakeBTreeNode();
	BTreeNode* bt3 = MakeBTreeNode();
	BTreeNode* bt4 = MakeBTreeNode();
	BTreeNode* bt5 = MakeBTreeNode();


	SetData(bt1, 1);
	SetData(bt2, 2);
	SetData(bt3, 3);
	SetData(bt4, 4);
	SetData(bt5, 5);

	MakeLeftSubTree(bt1, bt2);
	MakeRightSubTree(bt1, bt3);
	MakeLeftSubTree(bt2, bt4);
	MakeRightSubTree(bt2, bt5);

	InorderTraverse(bt1);
	printf("\n");
	PreorderTraverse(bt1);
	printf("\n");
	PostorderTraverse(bt1);
	printf("\n");
}
```


