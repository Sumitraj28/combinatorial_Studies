# 📈 Data Structures — Unit V: Complete Beginner-Friendly Notes

> **How to use these notes:** Read top to bottom. Every concept is explained with a simple analogy first, then the technical definition. Don't skip analogies — they are the key to truly *understanding* rather than just memorizing.

---

## 📌 Table of Contents

1. [Introduction to Data Structures](#1-introduction-to-data-structures)
2. [Arrays vs. Linked Lists](#2-arrays-vs-linked-lists)
3. [Stacks & Queues](#3-stacks--queues)
4. [Trees & Binary Search Trees (BST)](#4-trees--binary-search-tree-bst)
5. [Balanced Trees (AVL, Red-Black, B/B+ Trees)](#5-balanced-trees-avl-red-black-bb-trees)
6. [Graphs](#6-graphs)
7. [Hashing](#7-hashing)
8. [Heaps](#8-heaps)

---

## 1. Introduction to Data Structures

### 🧰 The Tool Organizer Analogy

Imagine you are a **carpenter**:
- If you dump all your nails, screws, hammers, and saws into a single bucket, finding a specific screw takes forever (**inefficient searching**).
- Instead, you buy a **toolbox with compartments**: a tray for screws, loops for screwdrivers, and a slot for the saw. 

Each compartment is designed for a specific tool. In programming, a **Data Structure** is that toolbox, organizing data so that operations (searching, inserting, deleting) are as fast and efficient as possible.

---

## 2. Arrays vs. Linked Lists

How do we store a list of items in memory? We have two main layouts:

### 🚂 2.1 The Array — "The Passenger Train"
**Analogy:** A passenger train with consecutive, numbered cabins. 
- If you have a ticket for Seat 5, you can walk directly to Cabin 5 (**$O(1)$ constant-time random access**).
- But if you want to add a new cabin in the middle of the train, you must decouple all subsequent cabins and shift them back (**$O(N)$ insertion cost**).

```
   Array (Contiguous Memory):
   ┌───────┬───────┬───────┬───────┬───────┐
   │ Seat 0│ Seat 1│ Seat 2│ Seat 3│ Seat 4│
   └───────┴───────┴───────┴───────┴───────┘
   Address: 0x100  0x104   0x108   0x10C   0x110  (consecutive)
```

---

### 🗺️ 2.2 The Linked List — "The Scavenger Hunt"
**Analogy:** A scavenger hunt. You are at Station A. You don't know where Station C is. You only know the clue pointing to Station B. When you reach Station B, you get the clue pointing to Station C.
- To find the last station, you must visit every station in between (**$O(N)$ sequential access**).
- But if you want to add a new station, you just write a new clue and update the pointers without moving any stations (**$O(1)$ insertion**).

```
   Linked List (Non-Contiguous Memory):
   ┌───────────┐      ┌───────────┐      ┌───────────┐
   │ Head:  10 ├───▶  │ Data:  20 ├───▶  │ Data:  30 ├───▶ NULL
   │ Next: 0x55│      │ Next: 0x99│      │ Next: NULL│
   └───────────┘      └───────────┘      └───────────┘
   Address: 0x11      Address: 0x55      Address: 0x99  (scattered)
```

---

### 📊 2.3 Detailed Comparison

| Feature | Array | Linked List |
| :--- | :--- | :--- |
| **Size** | Fixed at allocation. | Dynamic (grows and shrinks at runtime). |
| **Memory Allocation**| Contiguous block of RAM. | Non-contiguous, allocated as nodes. |
| **Access Time** | **$O(1)$** (Direct access via index). | **$O(N)$** (Must traverse from Head). |
| **Insert/Delete** | **$O(N)$** (Requires element shifting). | **$O(1)$** (At a known node position). |
| **Cache Locality** | **Excellent** (Adjacent items pre-fetched).| **Poor** (Nodes scattered across memory). |
| **Memory Overhead** | None (only stores data). | High (each node stores data + pointer). |

---

### 🔄 2.4 Linked List Variants
1.  **Singly Linked List:** Each node contains a single pointer to the next node. Traverse is unidirectional.
2.  **Doubly Linked List (DLL):** Each node contains two pointers: `next` and `prev`. Enables bidirectional traversal.
3.  **Circular Linked List:** The last node's `next` pointer references the head node, forming a closed ring.

---

## 3. Stacks & Queues

Both are restricted linear structures where insert/delete operations happen at specific endpoints.

### 🥞 3.1 Stack (LIFO - Last In First Out)
**Analogy:** A pile of **cafeteria trays**. You add trays to the top, and you take trays from the top. The last tray placed is the first tray removed.

```
   Stack Operations:
          [ 30 ]  ◀── TOP (Push / Pop happens here)
          [ 20 ]
          [ 10 ]  ◀── BOTTOM
```
- **Operations:**
  - `push(x)`: Adds element to the top. (Raises *Stack Overflow* if full).
  - `pop()`: Removes and returns the top element. (Raises *Stack Underflow* if empty).
  - `peek()`: Returns the top element without removing it.
- **Applications:** Function call stacks in recursion, Undo/Redo operations, parenthesis matching compiler checks.

---

### 🚶 3.2 Queue (FIFO - First In First Out)
**Analogy:** A **queue line at a movie ticket counter**. The first person in line gets the ticket and leaves first.

```
   Queue Operations:
   ◀── Dequeue ── [ 10 ] [ 20 ] [ 30 ] ── Enqueue ──◀
                   Front         Rear
```
- **Operations:**
  - `enqueue(x)`: Adds element to the **Rear** of the queue.
  - `dequeue()`: Removes and returns the element from the **Front** of the queue.
- **Variants:**
  - **Circular Queue:** Pointers wrap around to index 0 when reaching the end of the array, preventing wasted space.
  - **Priority Queue:** Elements are dequeued based on priority rather than arrival order.
  - **Deque (Double-Ended Queue):** Insertions and deletions are allowed at both the Front and Rear.

---

## 4. Trees & Binary Search Tree (BST)

A **Tree** is a hierarchical, non-linear structure of nodes connected by edges, containing no cycles.

```
            ( 50 )          ← Root Node
           /      \
        ( 30 )  ( 70 )      ← Parent Nodes
        /    \      \
     ( 20 ) ( 40 ) ( 80 )   ← Leaf Nodes (No children)
```

- **Binary Tree:** A tree where every node has at most 2 children (Left and Right).
- **Binary Search Tree (BST):** A binary tree with the ordering property:
  - The value of the **left child** must be less than the parent node.
  - The value of the **right child** must be greater than the parent node.

### 📐 4.1 Binary Tree Properties
For a binary tree of height $h$ (where a single root node has $h=0$):
*   **Max nodes at level $l$** = $2^l$.
*   **Max total nodes in tree** = $2^{h+1} - 1$.
*   **Leaf Nodes Formula:** Let $n_0$ be the leaf count, and $n_2$ be the number of nodes with exactly 2 children:
    $$n_0 = n_2 + 1$$

---

### 🔄 4.2 Tree Traversals
Using the tree diagram above, let's trace the traversals:

#### 1. Inorder (Left $\to$ Root $\to$ Right)
- **Trace:** Go left as far as possible, read, read parent, go right.
- **Output:** `20 30 40 50 70 80`
- > ⚠️ **Must-Remember:** Inorder traversal of a BST always yields values in **sorted order**.

#### 2. Preorder (Root $\to$ Left $\to$ Right)
- **Trace:** Read root, go left, go right.
- **Output:** `50 30 20 40 70 80`

#### 3. Postorder (Left $\to$ Right $\to$ Root)
- **Trace:** Go left, go right, read root.
- **Output:** `20 40 30 80 70 50`

---

## 5. Balanced Trees (AVL, Red-Black, B/B+ Trees)

### ⚠️ The Skewed Tree Problem
If we insert sorted keys into a BST ($10, 20, 30, 40$):

```
     ( 10 )
         \
        ( 20 )
            \
           ( 30 )
               \
              ( 40 )  ← Degenerates into a Linked List!
```
The tree skews, and search times degrade from $O(\log N)$ to $O(N)$ sequential scans. To prevent this, we use **self-balancing trees**:

*   **AVL Tree:** A BST where the height difference (**Balance Factor**) between left and right subtrees of any node is at most $\pm 1$:
    $$\text{Balance Factor} = \text{Height}(Left) - \text{Height}(Right)$$
    If BF violates this ($\pm 2$), the tree performs **Rotations** (Single LL/RR, Double LR/RL) to restore balance.
*   **Red-Black Tree:** A self-balancing BST that uses a color flag (Red or Black) on nodes. It is less balanced than AVL but requires fewer rotations during insertions/deletions.
*   **B-Tree & B+ Tree:** Multi-way search trees (nodes have more than 2 children) designed to optimize secondary disk storage. By storing hundreds of keys in a single node, they minimize disk read operations, making them ideal for database indexing.

---

## 6. Graphs

A **Graph** is a set of vertices (nodes) connected by edges.

```
       [ A ] ─── (weight: 5) ─── [ B ]
         │                         │
         │                         │
      (weight: 2)               (weight: 1)
         │                         │
         ▼                         ▼
       [ C ] ──────────────────▶ [ D ]
```
- **Directed Graph:** Edges have arrows indicating direction (e.g., $C \to D$).
- **Weighted Graph:** Edges have values representing costs/distances.

### 📊 6.1 Adjacency Matrix vs. Adjacency List

How do we represent a graph in code?

#### 1. Adjacency Matrix
A 2D array of size $V \times V$.
- *Pros:* Constant time ($O(1)$) to check if an edge exists between two nodes.
- *Cons:* Always consumes $O(V^2)$ space, which is wasteful for sparse graphs (graphs with few edges).

#### 2. Adjacency List
An array of lists of size $V$. Slot $i$ contains a list of all vertices adjacent to node $i$.
- *Pros:* Space-efficient ($O(V + E)$), making it ideal for sparse graphs.
- *Cons:* Checking if an edge exists requires traversing a list ($O(V)$ time).

---

### 🔀 6.2 Graph Traversals
*   **Breadth-First Search (BFS):**
    - **Analogy:** Slicing a stone into a quiet pond. ripples spread outward in concentric circles.
    - **Method:** Explores all neighbors at the current level before moving to the next. Uses a **Queue**.
    - **Application:** Finding the shortest path in an unweighted graph.
*   **Depth-First Search (DFS):**
    - **Analogy:** Exploring a maze. You walk down a path until you hit a wall, then backtrack to the last split.
    - **Method:** Explores deep down a branch before backtracking. Uses a **Stack** or **Recursion**.
    - **Application:** Cycle detection, Topological sorting.

---

## 7. Hashing

### 🗄️ The Storage Locker Analogy
Imagine a room with **100 storage lockers** (indices 0 to 99). 
When you bring an item (e.g., Key: `"Alice"`), you run it through a formula (**Hash Function**):
- $h(\text{"Alice"}) = 37$.
You store Alice's file in locker 37. When you return to search for Alice, you re-run the formula, get 37, and open locker 37 immediately. This provides **$O(1)$ average search time**.

---

### 💥 7.1 Collisions
What if $h(\text{"Bob"}) = 37$ as well? Two different keys mapping to the same slot is a **Collision**.

#### Collision Resolution Methods:
1.  **Separate Chaining (Open Hashing):** Each slot in the hash table points to a linked list. Colliding items are appended to the list at that slot. (Load factor $\alpha$ can exceed 1.0).
2.  **Open Addressing (Closed Hashing):** All items are stored within the table itself. If a collision occurs, find another empty slot:
    *   *Linear Probing:* Check slots sequentially: $h(x), h(x)+1, h(x)+2, \dots$ (Causes *primary clustering*).
    *   *Quadratic Probing:* Check slots at quadratic intervals: $h(x) + i^2$.
    *   *Double Hashing:* Calculate probe steps using a second hash function: $h(x) + i \cdot h_2(x)$.

---

## 8. Heaps

A **Binary Heap** is a complete binary tree stored inside a contiguous array.

```
       Max-Heap:                     Array representation:
         ( 90 )                       Index: [0]  [1]  [2]  [3]  [4]  [5]
        /      \                      Value: [90] [80] [70] [30] [40] [10]
     ( 80 )  ( 70 )
     /    \  /
  ( 30 ) (40)(10)
```

### 📐 8.1 Heap Properties & Index Mappings
*   **Max-Heap:** Parent node value $\ge$ children. The maximum value is always at the root.
*   **Min-Heap:** Parent node value $\le$ children. The minimum value is always at the root.

#### Index Formulas (0-Indexed Array)
For any node at index $i$:
- **Left Child Index:** $2i + 1$
- **Right Child Index:** $2i + 2$
- **Parent Index:** $\lfloor (i - 1) / 2 \rfloor$

### ⚙️ 8.2 Heap Operations
*   **Heapify:** The process of restoring heap properties by swapping a node down the tree ($O(\log N)$ time).
*   **Build Heap:** Converting a raw array into a heap. By processing nodes bottom-up, this takes **$O(N)$** time.
*   **Insert / Extract Min-Max:** Takes **$O(\log N)$** time (requires swapping nodes up or down the height of the tree).
*   **Heapsort:** Sorts an array by repeatedly extracting the root element ($O(N \log N)$ time in all cases).
