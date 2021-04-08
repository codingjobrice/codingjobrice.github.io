---
layout: single
title: Day 26 PreorderTraversal
---

전위 순회 알고리즘이다.

```{.cpp}
#include <stdio.h>
#include <malloc.h>


typedef struct _node {
	int data;
	_node* left;
	_node* right;
}Node;

void Preorder(Node* node) {
	if (node) {
    printf("%d\n", node->data);
		Preorder(node->left);
		Preorder(node->right);
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
