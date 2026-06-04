# Unit V: Data Structures - MCQ Bank

Master Arrays, Linked Lists, Stacks, Queues, Trees, Graphs, Hashing, and Heaps with these 50 solved, high-probability Multiple Choice Questions.

---

## 🔷 Topic 1: Arrays & Linked Lists

#### Q1. Which of the following is the primary advantage of an Array over a Linked List?
- A) Dynamic memory allocation
- B) $O(1)$ random access time
- C) $O(1)$ insertion at any position
- D) Low memory overhead for pointers
- **Answer: ✅ B**
- **Explanation**: Arrays store elements contiguously, allowing direct index calculations ($O(1)$ access). Linked lists require traversing pointers sequentially ($O(N)$ access).

#### Q2. In a Singly Linked List, inserting a new node at the beginning (head) of a list of size $N$ takes how much time?
- A) $O(1)$
- B) $O(N)$
- C) $O(\log N)$
- D) $O(N \log N)$
- **Answer: ✅ A**
- **Explanation**: Inserting at the head requires creating a node, pointing its next pointer to the current head, and updating the head pointer. This takes $O(1)$ constant time regardless of list size.

#### Q3. What is the main characteristic of a Doubly Linked List (DLL)?
- A) The last node points back to the first node
- B) Each node contains two data fields
- C) Each node contains pointers to both the next and the previous nodes, enabling bidirectional traversal
- D) It does not support deletion
- **Answer: ✅ C**
- **Explanation**: DLL nodes store data, a `next` pointer, and a `prev` pointer. Singly linked lists only store data and a `next` pointer.

#### Q4. In a Circular Singly Linked List, the `next` pointer of the last node points to:
- A) NULL
- B) The second node
- C) The head (first) node
- D) A random memory location
- **Answer: ✅ C**
- **Explanation**: In circular lists, the last node points back to the head node, forming a closed loop.

#### Q5. Array insertion at a random index in the worst case takes $O(N)$ time because:
- A) Memory must be reallocated
- B) Elements must be shifted to make room for the new element
- C) Pointers must be updated
- D) The array must be sorted first
- **Answer: ✅ B**
- **Explanation**: Inserting at the beginning or middle of an array requires shifting subsequent elements forward to maintain contiguous storage.

---

## 🔷 Topic 2: Stacks & Queues

#### Q6. A Stack operates on which access principle?
- A) First-In, First-Out (FIFO)
- B) Last-In, First-Out (LIFO)
- C) Highest Priority First
- D) Random Access
- **Answer: ✅ B**
- **Explanation**: Stacks restrict access to a single end (the Top). The last element pushed is the first element popped.

#### Q7. The condition of trying to pop an element from an empty stack is called:
- A) Stack Overflow
- B) Stack Underflow
- C) Null Pointer Exception
- D) Memory Leak
- **Answer: ✅ B**
- **Explanation**: Stack Overflow occurs when pushing onto a full stack. Stack Underflow occurs when popping from an empty stack.

#### Q8. Which of the following is a classic application of a Stack?
- A) Print job spooler queue
- B) CPU round robin scheduling
- C) Recursive function call management
- D) Shortest path routing in networks
- **Answer: ✅ C**
- **Explanation**: The OS uses a call stack to keep track of active function frames, return addresses, and local variables.

#### Q9. A Queue operates on which access principle?
- A) LIFO
- B) FIFO
- C) Random Access
- D) Min-Heap order
- **Answer: ✅ B**
- **Explanation**: Queues insert elements at the Rear and remove them from the Front, ensuring first-in-first-out order.

#### Q10. In a standard linear queue implemented using an array, dequeue operations cause:
- A) Stack Overflow
- B) Unused empty spaces at the front of the array that cannot be reclaimed
- C) Memory leaks
- D) Tree skewing
- **Answer: ✅ B**
- **Explanation**: As elements are dequeued, the front pointer moves forward, leaving unused indices at the front of the array. A **Circular Queue** solves this by wrapping pointers back to index 0.

#### Q11. Which data structure is used to convert an Infix expression (e.g., `A + B * C`) to a Postfix expression (e.g., `A B C * +`)?
- A) Queue
- B) Binary Tree
- C) Stack
- D) Heap
- **Answer: ✅ C**
- **Explanation**: A stack is used to temporarily store operators and enforce precedence rules during conversion.

---

## 🔷 Topic 3: Trees & Binary Search Trees (BST)

#### Q12. In a binary tree, what is the maximum number of nodes possible at level $l$ (where the root is at level 0)?
- A) $l$
- B) $2^l$
- C) $2^{l+1}$
- D) $2^l - 1$
- **Answer: ✅ B**
- **Explanation**: 
  - Level 0 (Root) can have $2^0 = 1$ node.
  - Level 1 can have $2^1 = 2$ nodes.
  - Level 2 can have $2^2 = 4$ nodes.
  - Generalizing, Level $l$ can have a maximum of $2^l$ nodes.

#### Q13. If a binary tree has height $h$ (where the root has height 0), what is the maximum total number of nodes in the tree?
- A) $2^h$
- B) $2^{h+1} - 1$
- C) $2^h + 1$
- D) $2^{h-1}$
- **Answer: ✅ B**
- **Explanation**: A full binary tree of height $h$ contains $\sum_{i=0}^{h} 2^i = 2^{h+1} - 1$ nodes.

#### Q14. In any binary tree, if the number of leaf nodes (nodes with 0 children) is $n_0$, and the number of nodes with exactly 2 children is $n_2$, then:
- A) $n_0 = n_2$
- B) $n_0 = n_2 + 1$
- C) $n_0 = n_2 - 1$
- D) $n_0 = 2 \times n_2$
- **Answer: ✅ B**
- **Explanation**: In a binary tree, the number of leaves is always one more than the number of nodes with two children ($n_0 = n_2 + 1$).

#### Q15. A Binary Search Tree (BST) is characterized by which property?
- A) The root is always the minimum element
- B) Every node's children must have the same height
- C) The left subtree contains values less than the parent node, and the right subtree contains values greater
- D) The tree is always balanced
- **Answer: ✅ C**
- **Explanation**: The left-smaller, right-larger property defines a BST, enabling efficient search, insertion, and deletion.

#### Q16. Traversing a Binary Search Tree (BST) using which traversal method yields values in sorted order?
- A) Preorder
- B) Inorder
- C) Postorder
- D) Level Order
- **Answer: ✅ B**
- **Explanation**: Inorder traversal visits nodes in Left $\to$ Root $\to$ Right order, which matches the sorted order of a BST.

#### Q17. What is the worst-case search complexity in a standard Binary Search Tree of size $N$?
- A) $O(1)$
- B) $O(\log N)$
- C) $O(N)$
- D) $O(N \log N)$
- **Answer: ✅ C**
- **Explanation**: In the worst case (skewed tree where elements are inserted in sorted order), the BST degenerates into a linear list, making search complexity $O(N)$.

#### Q18. What is the balance factor of a node in an AVL tree?
- A) Height(Left Subtree) + Height(Right Subtree)
- B) Height(Left Subtree) - Height(Right Subtree)
- C) Height(Root) - Height(Leaf)
- D) Number of Left Children / Number of Right Children
- **Answer: ✅ B**
- **Explanation**: The balance factor is the difference in height between the left and right subtrees. In an AVL tree, it must be $-1$, $0$, or $+1$.

#### Q19. B+ Trees are preferred over standard binary search trees for database indexing because:
- A) They use less memory
- B) They are simpler to implement
- C) All data records are stored in leaf nodes and leaves are linked, making range queries and disk reads highly efficient
- D) They do not suffer from collisions
- **Answer: ✅ C**
- **Explanation**: B+ trees store all data records in leaf nodes linked in a sequential list. This speeds up range queries and minimizes disk reads.

---

## 🔷 Topic 4: Graphs

#### Q20. In graph representation, what is the space complexity of an Adjacency Matrix for a graph with $V$ vertices?
- A) $O(V)$
- B) $O(V + E)$
- C) $O(V^2)$
- D) $O(E)$
- **Answer: ✅ C**
- **Explanation**: An adjacency matrix is a 2D array of size $V \times V$, requiring $O(V^2)$ space regardless of the number of edges.

#### Q21. Which graph representation is most space-efficient for a sparse graph (a graph with few edges)?
- A) Adjacency Matrix
- B) Adjacency List
- C) Incidence Matrix
- D) Complete Graph Matrix
- **Answer: ✅ B**
- **Explanation**: An adjacency list requires $O(V + E)$ space, making it highly efficient for sparse graphs where $E \ll V^2$.

#### Q22. Breadth-First Search (BFS) on a graph uses which helper data structure?
- A) Stack
- B) Queue
- C) Binary Heap
- D) Hash Table
- **Answer: ✅ B**
- **Explanation**: BFS explores nodes level-by-level using a FIFO queue. DFS uses a LIFO stack or recursion.

#### Q23. Which graph traversal is preferred for cycle detection in a directed graph and generating topological sorts?
- A) BFS
- B) DFS
- C) Kruskal's
- D) Binary Search
- **Answer: ✅ B**
- **Explanation**: DFS's backtracking model enables cycle detection (via back edges) and topological sorting.

---

## 🔷 Topic 5: Hashing

#### Q24. What is a collision in a hash table?
- A) The hash function returns an index larger than the table size
- B) Two distinct keys map to the same index
- C) A key is deleted from the table
- D) The table runs out of memory
- **Answer: ✅ B**
- **Explanation**: Collisions occur when $h(k_1) = h(k_2)$ for $k_1 \neq k_2$.

#### Q25. In separate chaining collision resolution:
- A) Collisions are resolved by finding the next empty slot in the table
- B) Collisions are stored in a linked list at each table index
- C) The load factor $\alpha$ must remain $\le 1.0$
- D) Deletions are extremely complex
- **Answer: ✅ B**
- **Explanation**: Separate chaining creates a linked list at each index. Because slots can hold multiple nodes, the load factor ($\alpha = N/M$) can exceed $1.0$.

#### Q26. Linear probing resolves collisions by:
- A) Creating a binary tree at each slot
- B) Searching slots sequentially ($h(x), h(x)+1, h(x)+2, \dots$) for the next available position
- C) Re-hashing the key using a second hash function
- D) Throwing a runtime exception
- **Answer: ✅ B**
- **Explanation**: Linear probing scans table slots sequentially. However, it is susceptible to **primary clustering** (long runs of occupied slots).

#### Q27. The load factor $\alpha$ of a hash table with $N$ elements and $M$ slots is defined as:
- A) $M / N$
- B) $N / M$
- C) $N + M$
- D) $N \times M$
- **Answer: ✅ B**
- **Explanation**: The load factor $\alpha = N / M$ measures table fullness.

---

## 🔷 Topic 6: Heaps

#### Q28. A Binary Heap is:
- A) A complete binary tree
- B) A skewed binary search tree
- C) A multi-way search tree
- D) An acyclic graph
- **Answer: ✅ A**
- **Explanation**: Heaps are complete binary trees (filled at all levels except possibly the lowest, which is filled from left to right), allowing them to be represented inside a contiguous array.

#### Q29. In a Max-Heap represented as a 1-indexed array, if a parent node is located at index $i$, where is its right child located?
- A) $2i$
- B) $2i + 1$
- C) $i / 2$
- D) $i + 1$
- **Answer: ✅ B**
- **Explanation**: 
  - Left child = $2i$.
  - Right child = $2i + 1$.
  - Parent = $\lfloor i/2 \rfloor$.

#### Q30. What is the time complexity to insert a new element into a Binary Heap of size $N$?
- A) $O(1)$
- B) $O(N)$
- C) $O(\log N)$
- D) $O(N \log N)$
- **Answer: ✅ C**
- **Explanation**: Insertion appends the element at the end of the array and bubbles it up to restore heap properties, taking at most $O(\log N)$ height swaps.

#### Q31. What is the time complexity of the Heap Sort algorithm in the average and worst cases?
- A) $O(N^2)$
- B) $O(N \log N)$
- C) $O(N)$
- D) $O(\log N)$
- **Answer: ✅ B**
- **Explanation**: Heap sort takes $O(N \log N)$ time in both average and worst cases because it performs $N$ extractions on a heap of height $\log N$.

#### Q32. What is the time complexity to build a binary heap from a raw array of $N$ elements?
- A) $O(N^2)$
- B) $O(N \log N)$
- C) $O(N)$
- D) $O(\log N)$
- **Answer: ✅ C**
- **Explanation**: Building a heap bottom-up using the Floyd's method takes $O(N)$ time.

---

## 🔷 Topic 7: Conceptual Review Questions

#### Q33. A queue where elements can be inserted or deleted at both ends is called:
- A) Priority Queue
- B) Circular Queue
- C) Deque (Double-Ended Queue)
- D) LIFO Queue
- **Answer: ✅ C**
- **Explanation**: Deque allows push/pop operations at both the Front and Rear.

#### Q34. What is the height of a balanced AVL tree containing $N$ nodes?
- A) $O(1)$
- B) $O(\log N)$
- C) $O(N)$
- D) $O(N^2)$
- **Answer: ✅ B**
- **Explanation**: AVL trees remain balanced, guaranteeing $O(\log N)$ height and search times.

#### Q35. If the Inorder traversal of a binary tree is `D B E A F C` and its Preorder traversal is `A B D E C F`, what is the Postorder traversal of the tree?
- A) `D E B F C A`
- B) `D E B F A C`
- C) `D B E F C A`
- D) `A B C D E F`
- **Answer: ✅ A**
- **Explanation**: 
  - Preorder starts with `A` (Root).
  - Split Inorder by `A`: Left subtree is `D B E`, Right subtree is `F C`.
  - Repeat for subtrees. The tree is:
    - Root: `A`
    - Left Child: `B` (with children `D` and `E`)
    - Right Child: `C` (with left child `F`)
  - Postorder (Left $\to$ Right $\to$ Root) is `D E B F C A`.

#### Q36. A binary tree in which every internal node has exactly 0 or 2 children is called a:
- A) Full Binary Tree (Strict Binary Tree)
- B) Complete Binary Tree
- C) Perfect Binary Tree
- D) Skewed Binary Tree
- **Answer: ✅ A**
- **Explanation**: A Full (Strict) binary tree requires that no node has exactly 1 child.

#### Q37. What is the worst-case space complexity of Depth-First Search (DFS) on a tree of height $H$?
- A) $O(1)$
- B) $O(H)$
- C) $O(N)$
- D) $O(2^H)$
- **Answer: ✅ B**
- **Explanation**: DFS uses a recursion stack. The maximum number of stack frames matches the height of the tree ($O(H)$).

#### Q38. Which data structure is best suited for implementing a FIFO printer spooler?
- A) Stack
- B) Binary Search Tree
- C) Queue
- D) Min-Heap
- **Answer: ✅ C**
- **Explanation**: A printer spooler processes print jobs in the order they arrive (FIFO), which is implemented using a queue.

#### Q39. In a hash table using quadratic probing, if a collision occurs at hash index $h(k)$, what is the sequence of probe positions?
- A) $h(k), h(k)+1, h(k)+2$
- B) $h(k), h(k)+1^2, h(k)+2^2, h(k)+3^2$
- C) $h(k), h(k) \times 2, h(k) \times 4$
- D) $h(k), h(k) + h_2(k)$
- **Answer: ✅ B**
- **Explanation**: Quadratic probing resolves collisions by checking slots at quadratic intervals: $(h(k) + i^2) \pmod m$.

#### Q40. Which of the following is true about a B-Tree?
- A) It is a binary search tree
- B) All leaf nodes must be at the same level
- C) It does not allow multiple keys in a node
- D) It has a height of $O(N)$
- **Answer: ✅ B**
- **Explanation**: B-Trees are balanced multi-way search trees where all leaf nodes are at the same level.

#### Q41. In a Min-Heap, the root node contains:
- A) The maximum element
- B) The minimum element
- C) The median element
- D) A random element
- **Answer: ✅ B**
- **Explanation**: A min-heap maintains the property that the parent is less than or equal to its children, placing the minimum value at the root.

#### Q42. Adjacency lists are preferred over adjacency matrices for:
- A) Complete graphs
- B) Sparse graphs
- C) Direct edge lookup speed
- D) Small graphs
- **Answer: ✅ B**
- **Explanation**: Adjacency lists use memory proportional to edges ($O(V+E)$), making them ideal for sparse graphs.

#### Q43. What is the time complexity to search for an element in a Hash Table under the worst-case scenario (e.g., all keys collide)?
- A) $O(1)$
- B) $O(\log N)$
- C) $O(N)$
- D) $O(N \log N)$
- **Answer: ✅ C**
- **Explanation**: In the worst-case scenario where all elements collide at a single index, search time degrades to traversing a linked list of size $N$ ($O(N)$).

#### Q44. The DFS traversal of a graph is equivalent to:
- A) Level order traversal of a tree
- B) Preorder traversal of a tree
- C) Inorder traversal of a tree
- D) Postorder traversal of a tree
- **Answer: ✅ B**
- **Explanation**: DFS visits nodes as deep as possible before backtracking, similar to a preorder traversal.

#### Q45. In a circular queue of size $M$, if the Front is at index 2 and the Rear is at index $M-1$, what happens if we attempt to enqueue a new element?
- A) Queue Underflow
- B) The element is inserted at index 0, and Rear is updated to 0
- C) Queue Overflow
- D) Pointers become invalid
- **Answer: ✅ B**
- **Explanation**: In a circular queue, the Rear pointer wraps around to index 0 if space is available (since Front is at index 2, slots 0 and 1 are empty).

#### Q46. An AVL tree is a:
- A) Multi-way search tree
- B) Self-balancing Binary Search Tree
- C) Complete Binary Tree
- D) Unordered heap
- **Answer: ✅ B**
- **Explanation**: AVL trees are self-balancing BSTs that maintain height balance to ensure $O(\log N)$ operations.

#### Q47. If the balance factor of a node in an AVL tree becomes $+2$ because of an insertion in the left subtree of the left child, what rotation is needed?
- A) Left Rotation (RR)
- B) Right Rotation (LL)
- C) Left-Right Rotation (LR)
- D) Right-Left Rotation (RL)
- **Answer: ✅ B**
- **Explanation**: A left-left (LL) imbalance requires a single Right Rotation to restore balance.

#### Q48. What is the space complexity of a complete binary tree stored inside an array?
- A) $O(V^2)$
- B) $O(N)$
- C) $O(2^N)$
- D) $O(N \log N)$
- **Answer: ✅ B**
- **Explanation**: Complete binary trees can be stored compactly in an array of size $N$ without gaps, taking $O(N)$ space.

#### Q49. Which hashing technique uses a second hash function to resolve collisions?
- A) Linear Probing
- B) Double Hashing
- C) Quadratic Probing
- D) Separate Chaining
- **Answer: ✅ B**
- **Explanation**: Double hashing calculates probe indices using: $(h_1(x) + i \cdot h_2(x)) \pmod m$.

#### Q50. In a Max-Heap, where is the second largest element located?
- A) At the root
- B) As a leaf node
- C) At either the left child or the right child of the root node
- D) In the left subtree only
- **Answer: ✅ C**
- **Explanation**: The largest element is at the root. The second largest must be one of its children (index 2 or index 3).
