---
layout: single
title: "Binary Search Tree 3"
categories: 
 - Data Structures
tags:
 - binary search tree
 - C++
 - data structure
---

### *Binary Search Tree 3*

#### Using C++



**bst3.h [header file]**

```c++
#pragma once
#ifndef BST_H
#define BST_H

#include <iostream>
#include <string>
#include <queue>
using namespace std;

template <class K, class E> class BST; 

template <class K, class E>
class TreeNode {
	friend class BST<K, E>;
	TreeNode(K ky, E el, TreeNode<K, E>* left = 0, TreeNode<K, E>* right = 0)
		: key(ky), element(el), leftChild(left), rightChild(right) { }

private:
	TreeNode<K, E>* leftChild;
	K key;
	E element;
	TreeNode<K, E>* rightChild;
};

template <class K, class E>
class BST {
public:
	BST() { root = 0; } // empty BST
	void Insert(K& newkey, E& el) { Insert(root, newkey, el); }
	bool Find(const K&, E&);
	void Delete(K& oldkey) { Delete(root, oldkey); }
	void Preorder() { Preorder(root); }
	void Inorder() { Inorder(root); }
	void Postorder() { Postorder(root); }
	void Levelorder();
private:  // helper functions
	void Visit(TreeNode<K, E>*);
	void Insert(TreeNode<K, E>*&, K&, E&);
	void Delete(TreeNode<K, E>*&, K&);
	void Preorder(TreeNode<K, E>*);
	void Inorder(TreeNode<K, E>*);
	void Postorder(TreeNode<K, E>*);

	TreeNode<K, E>* root;
};

template <class K, class E>
void BST<K, E>::Visit(TreeNode<K, E>* ptr)
{
	cout << ptr->key << ":" << ptr->element << " ";
}

template <class K, class E>
void BST<K, E>::Insert(TreeNode<K, E>*& ptr, K& newkey, E& el) { // Insert's helper function
	if (ptr == 0) ptr = new TreeNode<K, E>(newkey, el);
	else if (newkey < ptr->key) Insert(ptr->leftChild, newkey, el);
	else if (newkey > ptr->key) Insert(ptr->rightChild, newkey, el);
	else ptr->element = el; // update element
}

template <class K, class E>
bool BST<K, E>::Find(const K& k, E& e)
{
	TreeNode<K, E>* ptr = root;
	while (ptr)
	{
		if (k < ptr->key)
			ptr = ptr->leftChild;
		else if (k > ptr->key)
			ptr = ptr->rightChild;
		else
		{
			e = ptr->element;
			return true;
		}
	}
	return false;
}

//******* added function: Delete() **************

template <class K, class E>
void BST<K, E>::Delete(TreeNode<K, E>*& ptr, K& oldkey)
{
	// delete the node whose key is oldkey in the tree whose root is ptr
	TreeNode<K, E>* tmpptr; TreeNode<K, E>* tmpparentptr;

	if (ptr == 0) return;         // if there is no such node, just return

	if (oldkey < ptr->key)        // find oldkey in left subtree and delete
		Delete(ptr->leftChild, oldkey);

	else if (oldkey > ptr->key)   // delete in right subtree
		Delete(ptr->rightChild, oldkey);

	else     // in case ptr node to delete that has oldkey is found:
	{	    // find a proper node out of Children and replace the current node 

		if (!ptr->leftChild && !ptr->rightChild) // if there are no Children
		{
			delete ptr; ptr = 0; return;
		}

		else if (ptr->leftChild && !ptr->rightChild)
			// make ptr point to that Child and delete the node pointed by the current ptr
		{
			tmpptr = ptr; ptr = ptr->leftChild; delete tmpptr; return;
		}

		else if (!ptr->leftChild && ptr->rightChild)
		{
			tmpptr = ptr; ptr = ptr->rightChild; delete tmpptr; return;
		}

		else {    // if there are both left and right Child:
			      // find 'the smallest node' in the right tree whose root is rc

			TreeNode<K, E>* rc = ptr->rightChild;   // subtree whose root is rc

			if (!rc->leftChild)    // if rc has no left Child then rc is the node 
			                       // { transfer the information of rc node's key/element/rightChild to ptr node
			                       //   delete rc node (delete rc); }
			{
				ptr->key = rc->key;
				ptr->element = rc->element;
				ptr->rightChild = rc->rightChild;
				delete rc;
				return;
			}

			else // if rc has the left Child, left Child of left Child of rc
			// { track the left Child to the end, and find the node that has the smallest key
			//   transfer key/element of that node to ptr node, 
			//   save the right Child of that node as the left Child of the parent node of that node
			//   and then delete that node; }  
			{
				tmpparentptr = rc;
				rc = rc->leftChild; // initialize
				while (1)
				{
					if (rc->leftChild)
					{
						tmpparentptr = rc;
						rc = rc->leftChild;
					}
					else
						break;
				}
				ptr->key = rc->key;
				ptr->element = rc->element;
				tmpparentptr->leftChild = rc->rightChild;
				delete rc;
				return;
			}
		}
	}
}


template <class K, class E>
void BST<K, E>::Preorder(TreeNode<K, E>* currentNode) { // Preorder's helper function
	if (currentNode) {
		Visit(currentNode);
		Preorder(currentNode->leftChild);
		Preorder(currentNode->rightChild);
	}
}

template <class K, class E>
void BST<K, E>::Inorder(TreeNode<K, E>* currentNode) { // Inorder's helper function
	if (currentNode) {
		Inorder(currentNode->leftChild);
		Visit(currentNode);
		Inorder(currentNode->rightChild);
	}
}

template <class K, class E>
void BST<K, E>::Postorder(TreeNode<K, E>* currentNode) { // Postorder's helper function
	if (currentNode) {
		Postorder(currentNode->leftChild);
		Postorder(currentNode->rightChild);
		Visit(currentNode);
	}
}

template <class K, class E>
void BST<K, E>::Levelorder()
{
	queue<TreeNode<K, E>* > q;
	TreeNode<K, E>* currentNode = root;
	while (currentNode) {
		Visit(currentNode);
		if (currentNode->leftChild) q.push(currentNode->leftChild);
		if (currentNode->rightChild) q.push(currentNode->rightChild);
		if (q.empty()) return;
		currentNode = q.front();
		q.pop();
	}
}
#endif
```



**bst3.cpp [source file]**

```c++
#include "bst3.h"  
#include <string>

int main()
{
    BST<string, double> tree;
    string command, str; double dval;

    while (cin >> command)
        if (command == "insert") {
            cin >> str >> dval; tree.Insert(str, dval);
        }
        else if (command == "delete") {
            cin >> str; tree.Delete(str);
        }
        else if (command == "print") {
            cout << endl << "Inorder traversal :   "; tree.Inorder();
            cout << endl << "Postorder traversal : "; tree.Postorder();
            cout << endl;
        }
        else if (command == "find") {
            cin >> str;
            if (tree.Find(str, dval))
                cout << "The value of " << str << " is " << dval << endl;
            else cout << "No such key : " << str << endl;
        }
        else
            cout << "Invalid command : " << command << endl;
}
```

