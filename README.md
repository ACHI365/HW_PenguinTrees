# Tree
Tree implementation


Trees are, besides lists, stacks and queues, another flexible data-structure with many applications. In general, a tree consists of nodes which may hava multiple successors. The topmost node which has no further predecessor is also called root node. The bottom nodes without successors are the leaves. All other nodes are called internal. Data are only stored in non-leaf nodes.

In this assignment a particular kind of trees is implemented, namely, sorted binary trees. Binary trees are trees where each node either has two successors (left and right), or none. Sorted means that at each node, the invariant holds that all elements stored in the left subtree are less or equal to the element in the node, which in turn is less or equal to all elements in the right subtree. Moreover, we want arbitrarily many elements to be stored inside the tree.

For the realization, we use the Composite pattern. In contrast to lists, we represent the empty data-structure not by means of null but by an object of the class Leaf. Consider the following UML diagram:

![image](https://user-images.githubusercontent.com/77834636/166437969-e5d48814-c519-40ea-a22f-72c9afd3c802.png)


The constructor of a tree should receive as parameter a comparator which determines the ordering of the elements. Initiall, root should be initialized as Leaf. The constructor of class InnerNode receives info as parameter, while left and right are initialized as Leaf objects.

When implementing any method, take care to exploit sortedness and inspec only those parts of the tree which are really necessary. The method contains, e.g., may not visit nodes which are excluded due to sortedness.
