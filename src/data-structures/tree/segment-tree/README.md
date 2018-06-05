# Segment Tree

A segment tree is a data structure designed to perform 
certain array operations efficiently - especially those 
involving range queries.

A common application is the [Range Minimum Query](https://en.wikipedia.org/wiki/Range_minimum_query) (RMQ) problem,
where we are given an array of numbers and need to 
support operations of updating values of the array and 
finding the minimum of a contiguous subarray. 
A segment tree implementation for the RMQ problem 
takes `O(n)` to initialize, and `O(log n)` per query or 
update. The "minimum" operation can be replaced by any 
array operation (such as sum).

A segment tree is a binary tree with contiguous 
sub-arrays as nodes. The root of the tree represents the 
whole array. The two children of the root represent the 
first and second halves of the array. Similarly, the 
children of each node corresponds to the two halves of 
the array corresponding to the node. If the array has 
size `n`, we can prove that the segment tree has size at 
most `4n`. Each node stores the minimum of its 
corresponding sub-array.

In the implementation, we do not explicitly store this 
tree structure, but represent it using a `4n` sized array.
The left child of node i is `2i+1` and the right child 
is `2i+2`. This is a standard way to represent segment 
trees, and lends itself to an efficient implementation.

We build the tree bottom up, with the value of each node 
being the minimum of its children's values. This will 
take time `O(n)`, with one operation for each node. Updates 
are also done bottom up, with values being recomputed 
starting from the leaf, and up to the root. The number 
of operations done is the height of the tree, which 
is `O(log n)`. To answer queries, each node splits the 
query into two parts, one sub-query for each child. 
If a query contains the whole subarray of a node, we 
can use the precomputed value at the node. Using this 
optimisation, we can prove that only `O(log n)` minimum 
operations are done.

![Segment Tree](https://www.geeksforgeeks.org/wp-content/uploads/segment-tree1.png)

## References

- [Wikipedia](https://en.wikipedia.org/wiki/Segment_tree)
- [YouTube](https://www.youtube.com/watch?v=ZBHKZF5w4YU&index=65&list=PLLXdhg_r2hKA7DPDsunoDZ-Z769jWn4R8)
- [GeeksForGeeks](https://www.geeksforgeeks.org/segment-tree-set-1-sum-of-given-range/)