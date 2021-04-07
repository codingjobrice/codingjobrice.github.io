---
layout: single
title: Day 25 InorderTraversal
---

노드로 연결한 이진트리의 순회 방법 중 하나인 중위 순회 알고리즘이다.

중위 순회의 순서는 왼쪽으로 이동, 노드 방문, 오른쪽으로 이동 하는 순서이다.

```{.cpp}
#include <stdio.h>
#include <malloc.h>


typedef struct _node {
	int data;
	_node* left;
	_node* right;
}Node;

void Inorder(Node* node) {
	if (node) {
		Inorder(node->left);
		printf("%d\n", node->data);
		Inorder(node->right);
	}
}


int main() {
	Node* node1 = (Node*)malloc(sizeof(Node));
	Node* node2 = (Node*)malloc(sizeof(Node));
	Node* node3 = (Node*)malloc(sizeof(Node));
	Node* node4 = (Node*)malloc(sizeof(Node));

	node1->data = 1;
	node2->data = 2;
	node3->data = 3;
	node4->data = 4;

	node1->left = node2;
	node1->right = node3;
	node2->left = node4;
	node2->right = NULL;
	node3->left = NULL;
	node3->right = NULL;
	node4->left = NULL;
	node4->right = NULL;

	Inorder(node1);

	free(node1);
	free(node2);
	free(node3);
	free(node4);
}
```
