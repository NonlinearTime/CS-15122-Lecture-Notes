# Chapter 16

罗海旻 U201514716

## Checkpoint 0

- Insert the keys 1,2 and 3 in the order 2, 1, 3 and draw the tree formed. Then insert the keys in the order 1,2,3. What do you notice?

1. 以1,2,3顺序插入

```mermaid
graph LR
	A((2));	
```

```mermaid
graph TB
	A((2))-->B((1))
```

```mermaid
graph TB
	A((2))-->B((1))
	A((2))-->C((3))
```

2. 以1,2,3顺序插入

```mermaid
graph LR
	A((1))
```



```mermaid
graph TB
	A((1))-->B((2))
```

```mermaid
graph TB
	A((1))-->B((2))
	B((2))-->C((3))
```

​	由上述可知，不同顺序插入树中，数的形状可能不同。

## Checkpoint 1

- Write a function elem bst_max(bst B) that returns the element with the maximum key in a given BST.

```c#
tree* bst_max_helper(tree *T)
//@requires is_ordtree(T);
//@requires T != NULL;
//@ensures \result->right == NULL;
{
  if (T->right == NULL) return T;
  else return bst_max_helper(T->right);
}

elem bst_max(bst B)
//@requires B != NULL;
{
  if (B->root == NULL) return NULL;
  return bst_max_helper(B->root)->data;
}
```

- Write a function int count_leaves(bst B) that counts the number of leaves in a given BST.

```c#
int count_leaves_helper(tree* T)
//@requires \result > 0 || T==NULL;
{
  if (T==NULL) return 0;
  if (T->left==NULL && T->right==NULL) return 1;
  //@assert T->left != NULL || T->right != NULL;
  return count_leaves_helper(T->left) + count_leaves_helper(T->right);
}
```

```mermaid
graph TD
	A-->D((13))
	D-->E((42))
	E-->F((20))
	E-->G((71))
	G-->H((73))
	A((75))-->B((92))
	B-->I((84))
	B-->C((99))
	C-->M((98))
```

```mermaid
graph TD
	A((89))
	
	
	
	B((89))-->C((79))
	
	B1((89))-->C1((45))
	B1((89))-->C2((79))
	
	B2((89))-->C3((45))
	B2((89))-->C4((79))
	C3-->D((58))
	
	B3((89))-->C5((45))
	B3((89))-->C6((79))
	C5-->D2((10))
	C5-->D1((58))
	
	
```



```mermaid
graph TD	
	Y1((58))-->Y2((45))
	Y2-->Y3((10))
	Y1-->Y4((79))
	Y4-->Y5((63))
	Y4-->Y6((89))
	
	
	X1((58))-->X2((31))
	X2-->X3((10))
	X2-->X7((45))
	X1-->X4((79))
	X4-->X5((63))
	X4-->X6((89))	
```

