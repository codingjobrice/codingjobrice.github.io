---
layout: single
title: Day 20 SimpleBinaryTree
---

이진트리를 간단하게 노드만 생성하여 구현해보았다.


```{.cpp}
#include <stdio.h>
#include <malloc.h>

typedef struct _node {
	int data;
	_node *left;
	_node* right;
}Node;

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
	
	printf("%d ", node1->left->left->data);

	free(node1);
	free(node2);
	free(node3);
	free(node4);
}
```
