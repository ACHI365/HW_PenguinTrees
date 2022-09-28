# HW_PenguinTrees
Tree implementation

Trees are, besides lists, stacks and queues, another flexible data-structure with many applications. In general, a tree consists of nodes which may hava multiple successors. The topmost node which has no further predecessor is also called root node. The bottom nodes without successors are the leaves. All other nodes are called internal. Data are only stored in non-leaf nodes.

In this assignment a particular kind of trees is implemented, namely, sorted binary trees. Binary trees are trees where each node either has two successors (left and right), or none. Sorted means that at each node, the invariant holds that all elements stored in the left subtree are less or equal to the element in the node, which in turn is less or equal to all elements in the right subtree. Moreover, we want arbitrarily many elements to be stored inside the tree.

For the realization, we use the Composite pattern. In contrast to lists, we represent the empty data-structure not by means of null but by an object of the class Leaf. Consider the following UML diagram:



The constructor of a tree should receive as parameter a comparator which determines the ordering of the elements. Initiall, root should be initialized as Leaf. The constructor of class InnerNode receives info as parameter, while left and right are initialized as Leaf objects.

When implementing any method, take care to exploit sortedness and inspec only those parts of the tree which are really necessary. The method contains, e.g., may not visit nodes which are excluded due to sortedness.

The methods are meant to do the following:

insert
adds the given element to the tree so that the invariant is preserved. For that the comparator is passed around. null should not be inserted into the tree.
toString
returns all elements of the tree as comma separated String. For that, a StringBuilder is used. Hint: All tests rely on insert and toString! There are no dedicated tests for toString.
size
returns the number of elements (InnerNodes) of the tree. The method should require no more than one line in each class.
remove
removes the given element from the tree. If the element occur multiple times, exactly one occurrence should be deleted. Subsequently, the invariant should again hold! The procedure therefore is as follows:
If the node holding the element to be removed, has just one or no InnerNode successor, then it is replaced with the successor or a leaf node, respectively.
Otherwise, the node with the element to be removed, receives the element from the leftmost inner node of the right subtree (i.e., the next element according to the ordering) and remove that node there. An auxiliary method here might be convenient.
contains
checks whether the given element occurs somewhere in the data-structure.
countMatches
returns the number of all elements in the tree which satisfy the given predicate predicate.
getAll
returns all elements satisfying the predicate, as an array. The parameter index specifies the respective next empty entry of the array. The elements should occur inside the array in exactly the same order as in the tree.
Realize a class PenguinTrees which provides the following methods:

getAgeTree
returns an empty tree in which penguins are ordered according to their age (youngest first);
getHeightTree
returns an empty tree in which penguins are ordered according to their height (tallest first);
getMinorsAmount
returns the number of under-age (younger than 5 years) penguins in the tree;
getEvenNames
returns an array of all penguins whose name consists of an even number of characters.
