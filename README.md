
<article class="markdown-body entry-content container-lg" itemprop="text"><h1 dir="auto"><a id="user-content-penguin-trees" class="anchor" aria-hidden="true" href="#penguin-trees"><svg class="octicon octicon-link" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M7.775 3.275a.75.75 0 001.06 1.06l1.25-1.25a2 2 0 112.83 2.83l-2.5 2.5a2 2 0 01-2.83 0 .75.75 0 00-1.06 1.06 3.5 3.5 0 004.95 0l2.5-2.5a3.5 3.5 0 00-4.95-4.95l-1.25 1.25zm-4.69 9.64a2 2 0 010-2.83l2.5-2.5a2 2 0 012.83 0 .75.75 0 001.06-1.06 3.5 3.5 0 00-4.95 0l-2.5 2.5a3.5 3.5 0 004.95 4.95l1.25-1.25a.75.75 0 00-1.06-1.06l-1.25 1.25a2 2 0 01-2.83 0z"></path></svg></a>Penguin Trees</h1>
<p dir="auto">Trees are, besides lists, stacks and queues, another flexible data-structure with many applications.
In general, a tree consists of nodes which may hava multiple successors.
The topmost node which has no further predecessor is also called root node. The bottom nodes without successors are the
leaves. All other nodes are called internal.
Data are only stored in non-leaf nodes.</p>
<p dir="auto">In this assignment a particular kind of trees is implemented, namely, sorted binary trees.
Binary trees are trees where each node either has two successors (<code>left</code> and <code>right</code>), or none.
Sorted means that at each node, the invariant holds that all elements stored in the left subtree
are less or equal to the element in the node, which in turn is less or equal to all elements in the right subtree.
Moreover, we want arbitrarily many elements to be stored inside the tree.</p>
<p dir="auto">For the realization, we use the Composite pattern. In contrast to lists, we represent the empty data-structure not by means of
<code>null</code> but by an object of the class <code>Leaf</code>.
Consider the following UML diagram:</p>
<p dir="auto"><a target="_blank" rel="noopener noreferrer nofollow" href="https://camo.githubusercontent.com/649ba6356c8dd540b4326327a563a038f3e1d7bd3990c3cd7c0ffff65adb5cdf/68747470733a2f2f73796e63616e6473686172652e6c727a2e64652f646c2f666945566b376a36643770377a515051524553424d6638762f626165756d652e706e67"><img alt="" src="https://camo.githubusercontent.com/649ba6356c8dd540b4326327a563a038f3e1d7bd3990c3cd7c0ffff65adb5cdf/68747470733a2f2f73796e63616e6473686172652e6c727a2e64652f646c2f666945566b376a36643770377a515051524553424d6638762f626165756d652e706e67" data-canonical-src="https://syncandshare.lrz.de/dl/fiEVk7j6d7p7zQPQRESBMf8v/baeume.png" style="max-width: 100%;"></a></p>
<p dir="auto">The constructor of a tree should receive as parameter a
<a href="https://docs.oracle.com/javase/7/docs/api/java/util/Comparator.html" rel="nofollow">comparator</a>
which determines the ordering of the elements.
Initiall, <code>root</code> should be initialized as <code>Leaf</code>.
The constructor of class <code>InnerNode</code> receives <code>info</code> as parameter, while <code>left</code> and <code>right</code> are initialized
as <code>Leaf</code> objects.</p>
<p dir="auto">When implementing any method, take care to exploit sortedness and inspec only those parts of the tree which are
really necessary.
The method <code>contains</code>, e.g., may not visit nodes which are excluded due to sortedness.</p>
<p dir="auto">The methods are meant to do the following:</p>
<ul dir="auto">
<li><div dir="auto"><div dir="auto">
    
    
    
    <span>insert</span>
</div>
</div>adds the given element to the tree so that the invariant is preserved.
For that the comparator is passed around.
<code>null</code> should not be inserted into the tree.</li>
<li><div dir="auto"><div dir="auto">
    
    
    
    <span>toString</span>
</div>
</div>returns all elements of the tree as comma separated <code>String</code>.
For that, a <a href="https://docs.oracle.com/javase/7/docs/api/java/lang/StringBuilder.html" rel="nofollow">StringBuilder</a> is used.
<em>Hint: All tests rely on insert and toString! There are no dedicated tests for toString.</em></li>
<li><div dir="auto"><div dir="auto">
    
    
    
    <span>size</span>
</div>
</div>returns the number of elements (InnerNodes) of the tree. The method should require no more than one line
in each class.</li>
<li><div dir="auto"><div dir="auto">
    
    
    
    <span>remove</span>
</div>
</div>removes the given element from the tree.
If the element occur multiple times, exactly one occurrence should be deleted.
Subsequently, the invariant should again hold!
The procedure therefore is as follows:<ul dir="auto">
<li>If the node holding the element to be removed, has just one or no <code>InnerNode</code> successor,
then it is replaced with the successor or a leaf node, respectively.</li>
<li>Otherwise, the node with the element to be removed, receives the element from the leftmost inner node of the
right subtree (i.e., the next element according to the ordering) and remove that node there.
An auxiliary method here might be convenient.</li></ul></li>
<li><div dir="auto"><div dir="auto">
    
    
    
    <span>contains</span>
</div>
</div>checks whether the given element occurs somewhere in the data-structure.</li>
<li><div dir="auto"><div dir="auto">
    
    
    
    <span>countMatches</span>
</div>
</div>returns the number of all elements in the tree which satisfy the given predicate <a href="https://docs.oracle.com/javase/8/docs/api/java/util/function/Predicate.html" rel="nofollow">predicate</a>.</li>
<li><div dir="auto"><div dir="auto">
    
    
    
    <span>getAll</span>
</div>
</div>returns all elements satisfying the predicate, as an array.
The parameter <code>index</code> specifies the respective next empty entry of the array.
The elements should occur inside the array in exactly the same order as in the tree.</li>
</ul>
<p dir="auto">Realize a class <code>PenguinTrees</code> which provides the following methods:</p>
<ul dir="auto">
<li><div dir="auto"><div dir="auto">
    
    
    
    <span>getAgeTree</span>
</div>
</div>returns an empty tree in which penguins are ordered according to their age (youngest first);</li>
<li><div dir="auto"><div dir="auto">
    
    
    
    <span>getHeightTree</span>
</div>
</div>returns an empty tree in which penguins are ordered according to their height (tallest first);</li>
<li><div dir="auto"><div dir="auto">
    
    
    
    <span>getMinorsAmount</span>
</div>
</div>returns the number of under-age (younger than 5 years) penguins in the tree;</li>
<li><div dir="auto"><div dir="auto">
    
    
    
    <span>getEvenNames</span>
</div>
</div>returns an array of all penguins whose name consists of an even number of characters.</li>
</ul>



</article>
