# Unit VI: Algorithms - MCQ Bank

Test your mastery of runtime analysis, recurrences, sorting benchmarks, Dynamic Programming, and Greedy strategies with these 50 solved, high-probability Multiple Choice Questions.

---

## 🔷 Topic 1: Complexity Analysis & Recurrences

#### Q1. Which asymptotic notation represents a mathematically tight bound (average case)?
- A) Big-O ($O$)
- B) Big-Omega ($\Omega$)
- C) Big-Theta ($\Theta$)
- D) Little-o ($o$)
- **Answer: ✅ C**
- **Explanation**: Big-O is an upper bound, Big-Omega is a lower bound, and Big-Theta is a tight bound (both upper and lower bound).

#### Q2. What is the correct order of growth rates from fastest (best) to slowest (worst)?
- A) $O(1) < O(N) < O(\log N) < O(N^2)$
- B) $O(1) < O(\log N) < O(N) < O(N \log N) < O(N^2) < O(2^N)$
- C) $O(\log N) < O(1) < O(N) < O(N^2)$
- D) $O(1) < O(N) < O(N \log N) < O(2^N) < O(N^2)$
- **Answer: ✅ B**
- **Explanation**: Constant time $O(1)$ is fastest, followed by logarithmic $O(\log N)$, linear $O(N)$, linearithmic $O(N \log N)$, quadratic $O(N^2)$, and exponential $O(2^N)$.

#### Q3. Solve the recurrence relation $T(N) = 2T(N/2) + N$ using the Master Theorem:
- A) $T(N) = \Theta(\log N)$
- B) $T(N) = \Theta(N)$
- C) $T(N) = \Theta(N \log N)$
- D) $T(N) = \Theta(N^2)$
- **Answer: ✅ C**
- **Explanation**: Here, $a=2, b=2, d=1$ since $f(N) = N = N^1$. 
  - Compare $\log_b a = \log_2 2 = 1$ with $d = 1$.
  - Since $d = \log_b a$ (Case 2 of the Master Theorem), the solution is $T(N) = \Theta(N^{\log_b a} \log N) = \Theta(N \log N)$.

#### Q4. Solve the recurrence relation $T(N) = T(N/2) + 1$:
- A) $T(N) = \Theta(\log N)$
- B) $T(N) = \Theta(N)$
- C) $T(N) = \Theta(N \log N)$
- D) $T(N) = \Theta(1)$
- **Answer: ✅ A**
- **Explanation**: This is the recurrence for Binary Search. $a=1, b=2, d=0$ since $f(N) = 1 = N^0$.
  - $\log_b a = \log_2 1 = 0$. Since $d = \log_b a = 0$ (Case 2), the solution is $T(N) = \Theta(N^0 \log N) = \Theta(\log N)$.

#### Q5. What is the time complexity of the following code snippet?
```cpp
for (int i = 0; i < n; i++) {
    for (int j = 1; j < n; j = j * 2) {
        // Constant time operation
    }
}
```
- A) $O(N^2)$
- B) $O(N \log N)$
- C) $O(N)$
- D) $O(\log N)$
- **Answer: ✅ B**
- **Explanation**: The outer loop runs $N$ times. The inner loop variable $j$ doubles each step, running $\log N$ times. Thus, the total complexity is $O(N \log N)$.

---

## 🔷 Topic 2: Sorting Algorithms

#### Q6. Which sorting algorithm has an optimal best-case time complexity of $O(N)$ when the input array is already sorted?
- A) Selection Sort
- B) Merge Sort
- C) Insertion Sort
- D) Heap Sort
- **Answer: ✅ C**
- **Explanation**: Insertion sort only performs one comparison per element and no shifts when the array is sorted, leading to a linear $O(N)$ runtime. Selection sort always performs $O(N^2)$ comparisons.

#### Q7. Which sorting algorithm is stable but requires $O(N)$ auxiliary space?
- A) Quick Sort
- B) Heap Sort
- C) Merge Sort
- D) Bubble Sort
- **Answer: ✅ C**
- **Explanation**: Merge sort requires a temporary array of size $N$ to merge sub-arrays, taking $O(N)$ space. It is a stable sort. Heap sort takes $O(1)$ space but is unstable.

#### Q8. What is the worst-case complexity of Quick Sort, and when does it occur?
- A) $O(N \log N)$, when the array is randomly shuffled
- B) $O(N^2)$, when the array is already sorted and the pivot is chosen as the first or last element
- C) $O(N^2)$, when the array has duplicate values
- D) $O(N \log N)$, when the pivot is the median
- **Answer: ✅ B**
- **Explanation**: If the array is sorted and the pivot is the first or last element, the partitions are unbalanced ($0$ and $N-1$ elements). This results in a recursion depth of $N$ and a total complexity of $O(N^2)$.

#### Q9. Which of the following sorting algorithms is NOT stable?
- A) Merge Sort
- B) Bubble Sort
- C) Insertion Sort
- D) Selection Sort
- **Answer: ✅ D**
- **Explanation**: Selection sort can swap non-adjacent duplicate elements, altering their relative order.

---

## 🔷 Topic 3: Divide & Conquer

#### Q10. The Divide and Conquer paradigm involves which three steps?
- A) Select, Sort, Merge
- B) Divide, Conquer, Combine
- C) Memoize, Tabulate, Solve
- D) Input, Process, Output
- **Answer: ✅ B**
- **Explanation**: It divides the problem into subproblems, conquers them recursively, and combines their solutions.

#### Q11. Which algorithm uses Divide and Conquer to multiply two matrices in $O(N^{2.81})$ time instead of the naive $O(N^3)$ time?
- A) Dijkstra's Algorithm
- B) Strassen's Matrix Multiplication
- C) Floyd-Warshall Algorithm
- D) Kruskal's Algorithm
- **Answer: ✅ B**
- **Explanation**: Strassen's algorithm uses algebraic groupings to reduce the number of recursive matrix multiplications from 8 to 7, bringing the runtime down to $O(N^{2.81})$.

#### Q12. Binary Search is a classic example of:
- A) Greedy Strategy
- B) Dynamic Programming
- C) Divide and Conquer (specifically Decrease and Conquer)
- D) Backtracking
- **Answer: ✅ C**
- **Explanation**: Binary Search divides the search space in half at each step, conquering the active half and discarding the other.

---

## 🔷 Topic 4: Dynamic Programming

#### Q13. What are the two core properties required to apply Dynamic Programming to a problem?
- A) Optimal Substructure and Greedy Choice
- B) Overlapping Subproblems and Optimal Substructure
- C) Independency and Base Cases
- D) Recursion and Backtracking
- **Answer: ✅ B**
- **Explanation**: DP requires overlapping subproblems (so subproblem results can be reused) and optimal substructure (so optimal subproblem solutions build the global optimal solution).

#### Q14. The difference between Memoization and Tabulation is:
- A) Memoization is bottom-up, Tabulation is top-down
- B) Memoization is recursive (top-down), Tabulation is iterative (bottom-up)
- C) Tabulation uses more memory than Memoization
- D) Memoization is used for greedy algorithms
- **Answer: ✅ B**
- **Explanation**: Memoization is a top-down approach that caches recursive calls. Tabulation is a bottom-up approach that fills an iteration table starting from the base cases.

#### Q15. What is the time complexity of the Dynamic Programming solution to the 0/1 Knapsack problem with $N$ items and a knapsack capacity of $W$?
- A) $O(N \log N)$
- B) $O(2^N)$
- C) $O(N \cdot W)$
- D) $O(N^2)$
- **Answer: ✅ C**
- **Explanation**: The DP table has size $(N+1) \times (W+1)$, taking $O(N \cdot W)$ time to compute. This is a pseudo-polynomial time complexity.

#### Q16. Which of the following is solved optimally using Dynamic Programming?
- A) Fractional Knapsack
- B) Huffman Coding
- C) Longest Common Subsequence (LCS)
- D) Minimum Spanning Tree
- **Answer: ✅ C**
- **Explanation**: LCS is a classic DP problem ($O(M \cdot N)$ complexity). Fractional Knapsack, Huffman Coding, and MST are solved using Greedy algorithms.

#### Q17. The Floyd-Warshall algorithm finds the shortest path between all pairs of nodes in a graph in:
- A) $O((V+E)\log V)$ time
- B) $O(V \cdot E)$ time
- C) $O(V^3)$ time
- D) $O(V^2)$ time
- **Answer: ✅ C**
- **Explanation**: Floyd-Warshall is a DP-based algorithm that uses three nested loops over the vertices, resulting in $O(V^3)$ runtime.

---

## 🔷 Topic 5: Greedy Algorithms

#### Q18. A Greedy algorithm:
- A) Guarantees an optimal solution for all problems
- B) Backtracks when a choice leads to a sub-optimal state
- C) Makes the locally optimal choice at each step without backtracking
- D) Solves all overlapping subproblems first
- **Answer: ✅ C**
- **Explanation**: Greedy algorithms make immediate, locally optimal choices and never backtrack, making them fast but not always globally optimal.

#### Q19. Huffman Coding is used for:
- A) Finding shortest paths in graphs
- B) Lossless data compression using variable-length codes
- C) Encryption
- D) Sorting strings
- **Answer: ✅ B**
- **Explanation**: Huffman coding assigns shorter binary codes to more frequent characters, optimizing data compression.

#### Q20. Dijkstra's Single-Source Shortest Path algorithm is a Greedy algorithm that:
- A) Works correctly on graphs with negative edge weights
- B) Requires $O(V^3)$ time
- C) Fails on graphs with negative edge weights
- D) Finds the Minimum Spanning Tree
- **Answer: ✅ C**
- **Explanation**: Dijkstra's algorithm assumes that once a vertex is visited, its shortest path is finalized. This assumption fails if there are negative edge weights.

#### Q21. Which algorithm constructs a Minimum Spanning Tree (MST) by sorting all edges by weight and adding them one by one if they do not create a cycle?
- A) Prim's Algorithm
- B) Dijkstra's Algorithm
- C) Kruskal's Algorithm
- D) Bellman-Ford Algorithm
- **Answer: ✅ C**
- **Explanation**: Kruskal's is an edge-based greedy algorithm that uses a Union-Find data structure to check for cycles while adding sorted edges.

#### Q22. Prim's MST algorithm builds the tree by:
- A) Sorting all edges in the graph
- B) Growing the tree vertex-by-vertex, adding the cheapest edge connected to the current tree
- C) Using dynamic programming
- D) Dividing the graph into sub-graphs
- **Answer: ✅ B**
- **Explanation**: Prim's is a vertex-based greedy algorithm. It starts at a root vertex and adds the cheapest edge connecting a visited vertex to an unvisited vertex.

---

## 🔷 Topic 6: Graph & String Algorithms

#### Q23. Which algorithm should be used to find the shortest path in a graph containing negative edge weights and detect negative weight cycles?
- A) Dijkstra's Algorithm
- B) Bellman-Ford Algorithm
- C) Floyd-Warshall Algorithm
- D) Kruskal's Algorithm
- **Answer: ✅ B**
- **Explanation**: Bellman-Ford runs in $O(V \cdot E)$ time. It handles negative weights and detects negative cycles by running a final relaxation step.

#### Q24. What is the time complexity of the Knuth-Morris-Pratt (KMP) string matching algorithm for a text of length $N$ and pattern of length $M$?
- A) $O(N \cdot M)$
- B) $O(N + M)$
- C) $O(N \log M)$
- D) $O(M \log N)$
- **Answer: ✅ B**
- **Explanation**: KMP precomputes a prefix function (pi array) in $O(M)$ time and searches the text in $O(N)$ time, avoiding backtracking over the text.

#### Q25. The Rabin-Karp string matching algorithm uses which technique to search for a pattern?
- A) A prefix tree (Trie)
- B) Rolling Hash function
- C) Dynamic programming
- D) Greedy choices
- **Answer: ✅ B**
- **Explanation**: Rabin-Karp calculates hash values for the pattern and for sliding windows of the text. It uses a rolling hash to update values in $O(1)$ time.

---

## 🔷 Topic 7: General Algorithmic Concepts

#### Q26. Space complexity measures:
- A) The physical disk space occupied by the program code
- B) The maximum RAM memory required by the algorithm during execution as a function of input size
- C) The CPU cache lines utilized
- D) The size of the compiler
- **Answer: ✅ B**
- **Explanation**: Space complexity measures the auxiliary memory needed by the algorithm during execution, excluding the input space itself.

#### Q27. What is the time complexity of building a heap of size $N$?
- A) $O(N)$
- B) $O(N \log N)$
- C) $O(\log N)$
- D) $O(N^2)$
- **Answer: ✅ A**
- **Explanation**: Floyd's heap construction method runs in $O(N)$ time by processing nodes bottom-up.

#### Q28. An algorithm with a time complexity of $O(2^N)$ is classified as:
- A) Polynomial time
- B) Logarithmic time
- C) Exponential time
- D) Factorial time
- **Answer: ✅ C**
- **Explanation**: $O(2^N)$ is exponential, meaning runtime doubles with each incremental addition to the input size.

#### Q29. In a greedy fractional knapsack problem, items are sorted by:
- A) Maximum value
- B) Minimum weight
- C) Value-to-weight ratio ($v_i / w_i$)
- D) Random selection
- **Answer: ✅ C**
- **Explanation**: Sorting items by value-to-weight ratio allows us to maximize total value by greedily taking the most valuable density items first.

#### Q30. The Bellman-Ford algorithm relax all edges in the graph how many times?
- A) $V$ times
- B) $V - 1$ times
- C) $E$ times
- D) $E - 1$ times
- **Answer: ✅ B**
- **Explanation**: The shortest path in a graph with $V$ vertices can contain at most $V-1$ edges. Thus, Bellman-Ford relaxes all edges $V-1$ times.

#### Q31. What is the recurrence relation for the Tower of Hanoi problem?
- A) $T(N) = T(N-1) + 1$
- B) $T(N) = 2T(N-1) + 1$
- C) $T(N) = 2T(N/2) + 1$
- D) $T(N) = T(N-2) + 2$
- **Answer: ✅ B**
- **Explanation**: Tower of Hanoi requires moving $N-1$ disks to an auxiliary peg ($T(N-1)$), moving the largest disk to the target peg ($1$), and moving the $N-1$ disks to the target peg ($T(N-1)$). This yields $T(N) = 2T(N-1) + 1$, which solves to $O(2^N)$.

#### Q32. What is the time complexity of the recursion tree representing the Fibonacci recurrence $T(N) = T(N-1) + T(N-2)$ without memoization?
- A) $O(N)$
- B) $O(\log N)$
- C) $O(2^N)$
- D) $O(N^2)$
- **Answer: ✅ C**
- **Explanation**: The recursion tree branches twice at each level, leading to an exponential number of redundant calculations ($O(2^N)$).

#### Q33. Dynamic Programming Fibonacci calculation takes how much time with memoization/tabulation?
- A) $O(N)$
- B) $O(2^N)$
- C) $O(N^2)$
- D) $O(\log N)$
- **Answer: ✅ A**
- **Explanation**: Caching subproblem results reduces the number of calculations to $N$, yielding a linear $O(N)$ runtime.

#### Q34. Topological sort is applicable to which type of graphs?
- A) Any directed graph
- B) Undirected graphs
- C) Directed Acyclic Graphs (DAGs)
- D) Complete graphs
- **Answer: ✅ C**
- **Explanation**: Topological sort orders vertices such that for every directed edge $U \to V$, $U$ comes before $V$. This is only possible if the graph is directed and contains no cycles (DAG).

#### Q35. What is the maximum number of edges in a Minimum Spanning Tree of a graph with $V$ vertices?
- A) $V$
- B) $V - 1$
- C) $V + 1$
- D) $E$
- **Answer: ✅ B**
- **Explanation**: An MST must connect all $V$ vertices without forming cycles, which requires exactly $V-1$ edges.

#### Q36. In Kruskal's algorithm, cycle detection is performed using which data structure?
- A) Stack
- B) Queue
- C) Disjoint Set Union (DSU / Union-Find)
- D) Hash Table
- **Answer: ✅ C**
- **Explanation**: DSU tracks connected components and checks if two vertices belong to the same set in near-constant time ($O(\alpha(V))$).

#### Q37. What is the runtime complexity of the naive string matching algorithm?
- A) $O(N + M)$
- B) $O(N \cdot M)$
- C) $O(N^2)$
- D) $O(M^2)$
- **Answer: ✅ B**
- **Explanation**: The naive algorithm shifts the pattern one character at a time and compares it against the text, taking $O(N \cdot M)$ time in the worst case.

#### Q38. In the Master Theorem, if $T(N) = 8T(N/2) + N^2$, the time complexity is:
- A) $\Theta(N^2)$
- B) $\Theta(N^3)$
- C) $\Theta(N^2 \log N)$
- D) $\Theta(N \log N)$
- **Answer: ✅ B**
- **Explanation**: $a=8, b=2 \implies N^{\log_2 8} = N^3$.
  - Compare $N^3$ with $f(N) = N^2$.
  - Since $f(N) = O(N^2) = O(N^{3-\epsilon})$ (Case 1), the solution is $T(N) = \Theta(N^3)$.

#### Q39. What is the space complexity of in-place Quick Sort in the average case?
- A) $O(1)$
- B) $O(N)$
- C) $O(\log N)$
- D) $O(N \log N)$
- **Answer: ✅ C**
- **Explanation**: Quick Sort is in-place (it doesn't use temporary arrays), but its recursive call stack requires $O(\log N)$ space on average.

#### Q40. Which algorithm is best suited for finding the shortest path between all pairs of vertices in a sparse graph?
- A) Floyd-Warshall
- B) Running Dijkstra's algorithm $V$ times with a binary heap
- C) Bellman-Ford
- D) Prim's
- **Answer: ✅ B**
- **Explanation**: For sparse graphs ($E \ll V^2$), running Dijkstra $V$ times takes $O(V \cdot E \log V)$ time, which is faster than Floyd-Warshall's $O(V^3)$ runtime.

#### Q41. In dynamic programming, the Matrix Chain Multiplication problem is solved in:
- A) $O(N)$ time
- B) $O(N \log N)$ time
- C) $O(N^2)$ time
- D) $O(N^3)$ time
- **Answer: ✅ D**
- **Explanation**: The DP recurrence calculates parenthesization options over three nested loops, taking $O(N^3)$ time.

#### Q42. The prefix function (LPS array) in KMP string matching stores:
- A) The hash values of substrings
- B) The length of the longest proper prefix that is also a suffix for each substring of the pattern
- C) Character frequencies
- D) Pointer jumps
- **Answer: ✅ B**
- **Explanation**: The LPS (Longest Prefix Suffix) array tells KMP how many characters of the pattern can be skipped during a mismatch.

#### Q43. What is the worst-case time complexity of the Rabin-Karp algorithm?
- A) $O(N + M)$
- B) $O(N \cdot M)$
- C) $O(N^2)$
- D) $O(M^2)$
- **Answer: ✅ B**
- **Explanation**: In the worst-case scenario (e.g., matching a pattern like `AAAA` in a text of `AAAAAA` where all hash values collide), Rabin-Karp performs character comparisons for every step, degrading to $O(N \cdot M)$ time.

#### Q44. An algorithm's space complexity includes:
- A) Only the stack memory
- B) Only the heap memory
- C) The input space and auxiliary space used during execution
- D) The source code size
- **Answer: ✅ C**
- **Explanation**: Total space complexity is the sum of the input space and the auxiliary space used by variables, structures, and the call stack.

#### Q45. Which data structure is used to implement a priority queue in Dijkstra's algorithm for optimal time complexity?
- A) Queue
- B) Min-Heap (or Fibonacci Heap)
- C) Stack
- D) BST
- **Answer: ✅ B**
- **Explanation**: A Min-Heap extracts the minimum distance vertex in $O(\log V)$ time, optimizing Dijkstra's runtime.

#### Q46. If an algorithm takes $T(N) = T(N-1) + O(1)$ time, its time complexity is:
- A) $O(1)$
- B) $O(\log N)$
- C) $O(N)$
- D) $O(N^2)$
- **Answer: ✅ C**
- **Explanation**: $T(N) = T(N-1) + c = T(N-2) + 2c = \dots = N \cdot c = O(N)$.

#### Q47. If an algorithm takes $T(N) = T(N-1) + O(N)$ time, its time complexity is:
- A) $O(N)$
- B) $O(N \log N)$
- C) $O(N^2)$
- D) $O(2^N)$
- **Answer: ✅ C**
- **Explanation**: $T(N) = T(N-1) + N = T(N-2) + (N-1) + N = \sum_{i=1}^{N} i = \frac{N(N+1)}{2} = O(N^2)$. This is the recurrence for Selection/Insertion sort.

#### Q48. Which sorting algorithm is stable and has a guaranteed time complexity of $O(N \log N)$ in all cases?
- A) Quick Sort
- B) Selection Sort
- C) Merge Sort
- D) Insertion Sort
- **Answer: ✅ C**
- **Explanation**: Merge sort divides the array in half and merges them in $O(N)$ time, guaranteeing $O(N \log N)$ runtime in the best, average, and worst cases.

#### Q49. The activity selection problem (greedy approach) selects the next activity based on:
- A) Earliest start time
- B) Earliest finish time
- C) Shortest duration
- D) Maximum profit
- **Answer: ✅ B**
- **Explanation**: Selecting the activity that finishes first leaves the maximum amount of time for subsequent activities.

#### Q50. Can the Master Theorem be used to solve the recurrence $T(N) = 2T(N/2) + N \log N$?
- A) Yes, directly
- B) No, because $f(N) = N \log N$ is not polynomial
- C) Yes, using Case 2 extension where $T(N) = \Theta(N \log^2 N)$
- D) No, because $a < 1$
- **Answer: ✅ C**
- **Explanation**: Although not solvable by the standard Master Theorem, the Case 2 extension ($f(N) = \Theta(N^{\log_b a} \log^k N)$ with $k=1$) yields $T(N) = \Theta(N \log^2 N)$.
