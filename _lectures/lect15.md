---
num: "lect15"
lecture_date: 2021-05-01
desc: "Binary Search Trees continued"
ready: true
annotatedready: false
---
## Relevant topics in the textbook:
Data Structures and Other Objects Using C++ Chapter 10

# Trees

* A collection of connected nodes
* One of the nodes is the "Root node"
* Each node can have many children nodes, but only a single parent node.

## Important terms:

* Root node
* Leaf node
* Subtree
* Parent node
* Key
* Level
* Degree

# Binary Trees

* Each node can have at most two children nodes


# Binary Search Trees

* The left subtree of a node contains only nodes with keys lesser than the node's key
* The right subtree of a node contains only nodes with keys greater than the node's key
* No duplicate nodes

Good visualizations can be found [here](https://visualgo.net/bn/bst) and [here](https://www.cs.usfca.edu/~galles/visualization/BST.html)


# Tree Traversal

Let's create a BST from a given list of elements: 5,2,7,3,8,4,6,1,9,10

How will it look like?

Let's check.

## Level-order Traversal (Breadth-First Search)

Visit all the nodes at given level from left to right.
Then repeat for next level.

Outcome for our example: 5 2 7 1 3 6 8 4 9 10


## Depth-first Search

### In-order Traversal

Visit left subtree, then the node, then right subtree

Outcome for our example: 1 2 3 4 5 6 7 8 9 10

### Pre-order Traversal

Visit the node, then left subtree, then right subtree

Outcome for our example: 5 2 1 3 4 7 6 8 9 10


### Post-order Traversal

Visit left subtree, then right subtree, then the node

Outcome for our example: 1 4 3 2 6 10 9 8 7 5
      

# Tree inversion

Tree mirroring

Recursive approach:
* Invert left subtree
* Invert right subtree
* Swap left and right subtrees
