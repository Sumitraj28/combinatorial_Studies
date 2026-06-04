# Unit V: DS Revision Cheat Sheet

A comprehensive study card covering data structure operations, time/space complexities, tree properties, and traversal techniques.

---

## ⚡ 1. Complexity & Formulas Card

### Time & Space Complexity Matrix
| Data Structure | Access (Avg/Worst) | Search (Avg/Worst) | Insert (Avg/Worst) | Delete (Avg/Worst)| Space Complexity |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Array** | $O(1) / O(1)$ | $O(N) / O(N)$ | $O(N) / O(N)$ | $O(N) / O(N)$ | $O(N)$ |
| **Singly LL** | $O(N) / O(N)$ | $O(N) / O(N)$ | $O(1) / O(1)$ | $O(1) / O(1)$ | $O(N)$ |
| **Stack (Array)**| $O(N) / O(N)$ | $O(N) / O(N)$ | $O(1) / O(1)$ | $O(1) / O(1)$ | $O(N)$ |
| **Queue (Array)**| $O(N) / O(N)$ | $O(N) / O(N)$ | $O(1) / O(1)$ | $O(1) / O(1)$ | $O(N)$ |
| **BST** | $O(\log N)/O(N)$ | $O(\log N)/O(N)$ | $O(\log N)/O(N)$ | $O(\log N)/O(N)$ | $O(N)$ |
| **AVL Tree** | $O(\log N)/O(\log N)$| $O(\log N)/O(\log N)$| $O(\log N)/O(\log N)$| $O(\log N)/O(\log N)$| $O(N)$ |
| **Hash Table** | N/A | $O(1) / O(N)$ | $O(1) / O(N)$ | $O(1) / O(N)$ | $O(N)$ |
| **Binary Heap** | N/A | $O(N) / O(N)$ | $O(\log N)/O(\log N)$| $O(\log N)/O(\log N)$| $O(N)$ |

### Binary Tree Properties Formulas
Let $h$ be the height of the tree (where a single root node has height 0):
*   **Max Nodes at Level $l$** = $2^l$.
*   **Max Total Nodes in a Binary Tree** = $2^{h+1} - 1$.
*   **Min Total Nodes in a Binary Tree** = $h + 1$ (skewed tree).
*   **Leaf Nodes vs. Degree-2 Nodes**: In any binary tree, let $n_0$ be the number of leaf nodes and $n_2$ be the number of nodes with exactly 2 children:
    $$n_0 = n_2 + 1$$

---

## 📊 2. High-Yield Summary Tables

### Graph Traversals Comparison
| Feature | Breadth-First Search (BFS) | Depth-First Search (DFS) |
| :--- | :--- | :--- |
| **Data Structure** | **Queue** (FIFO). | **Stack** (LIFO) or **Recursion**. |
| **Execution Path** | Visits all neighbor nodes first before moving deeper.| Explores deep down a branch before backtracking. |
| **Time Complexity** | $O(V + E)$ | $O(V + E)$ |
| **Space Complexity** | $O(V)$ (for Queue storage). | $O(V)$ (for recursion call stack). |
| **Key Use Case** | Finding the shortest path in an unweighted graph. | Cycle detection, Topological sort. |

### Heap Array Indirection Formulas (1-Indexed Array)
*   **Parent Node Index** of node $i$ = $\lfloor i / 2 \rfloor$.
*   **Left Child Index** of node $i$ = $2 \times i$.
*   **Right Child Index** of node $i$ = $2 \times i + 1$.
*   *(Note: For 0-indexed arrays: Parent = $\lfloor (i-1)/2 \rfloor$, Left Child = $2i+1$, Right Child = $2i+2$)*.

---

## 🧠 3. Memory Tricks & Mnemonics

*   **Tree Traversals**:
    *   **In**order: Left $\to$ **Root** $\to$ Right (Root is **in** the middle).
    *   **Pre**order: **Root** $\to$ Left $\to$ Right (Root is **pre**/before).
    *   **Post**order: Left $\to$ Right $\to$ **Root** (Root is **post**/after).
*   **DFS vs. BFS**:
    *   **D**FS $\to$ **D**eep (Stack/Recursion).
    *   **B**FS $\to$ **B**readth/Wide (Queue).
*   **Stack vs Queue**:
    *   Stack = **LIFO** (Last In, First Out).
    *   Queue = **FIFO** (First In, First Out).

---

## 🚨 4. High-Risk Confusion Zones

### 1. Inorder Traversal Sort Property
*   **Confusion**: Does Inorder traversal print all binary trees in sorted order?
*   **Reality**: **No**. Inorder traversal prints elements in sorted order **only** if the tree is a Binary Search Tree (BST). For general binary trees, it does not print values in sorted order.

### 2. Heap vs. Binary Search Tree (BST)
*   **Confusion**: Are Heaps and BSTs ordered the same way?
*   **Reality**: **No**. In a BST, the left child is smaller than the parent, and the right child is larger. In a Max-Heap, **both** children must be smaller than the parent (no left-to-right ordering). Consequently, you cannot search a Heap in $O(\log N)$ time; searching a Heap takes $O(N)$ time.

### 3. Hashing: Chaining vs. Open Addressing
*   **Chaining**: Collisions are placed in separate, dynamic linked lists. The Load Factor $\alpha = N / M$ can exceed $1.0$.
*   **Open Addressing**: Collisions must be resolved inside the pre-allocated table cells. The Load Factor $\alpha$ must be $\le 1.0$.

---

## ⚠️ 5. Traps & Mistakes to Avoid in Exams

*   **BST Skewed Tree Trap**: Do not assume BST operations are always $O(\log N)$. If keys are inserted in sorted order (e.g., $1, 2, 3, 4$), the BST degenerates into a skewed line, and search times degrade to $O(N)$. Self-balancing AVL trees are needed to guarantee $O(\log N)$.
*   **Heap Sort Array Bounds**: When performing heap calculations, double-check whether the problem assumes 1-based indexing or 0-based indexing for the array representation, as this changes child-parent index calculations.
*   **Recursion space overhead**: Even though DFS and tree traversals have $O(1)$ auxiliary space excluding the system stack, their actual runtime space complexity is $O(H)$ (where $H$ is the tree height) due to recursion stack frames.
